---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183409"
---
# <a name="pooling"></a>Sdružování
Tato ukázka ukazuje, jak rozšířit Windows Communication Foundation (WCF) pro podporu sdružování objektů. Ukázka ukazuje, jak vytvořit atribut, který je syntakticky `ObjectPoolingAttribute` a sémanticky podobný atribut funkce Enterprise Services. Sdružování objektů může poskytnout dramatické zvýšení výkonu aplikace. Může však mít opačný účinek, pokud není správně používán. Sdružování objektů pomáhá snížit režii opětovného vytvoření často používaných objektů, které vyžadují rozsáhlou inicializaci. Pokud však volání metody na sdružený objekt trvá značné množství času na dokončení, sdružování objektů fronty další požadavky, jakmile je dosaženo maximální velikost i fondu. Proto může selhat sloužit některé požadavky na vytvoření objektu vyvoláním výjimku časového času.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Prvním krokem při vytváření rozšíření WCF je rozhodnout bod rozšiřitelnosti použít.  
  
 V WCF termín *dispečer* odkazuje na součást za běhu odpovědné za převod příchozích zpráv na vyvolání metody ve službě uživatele a pro převod vrácené hodnoty z této metody na odchozí zprávu. Služba WCF vytvoří dispečera pro každý koncový bod. Klient WCF musí použít dispečera, pokud je smlouva přidružená k tomuto klientovi duplexní smlouvou.  
  
 Dispečeři kanálu a koncového bodu nabízejí rozšiřitelnost celého kanálu a kontraktu tím, že vystavují různé vlastnosti, které řídí chování dispečera. Vlastnost <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> také umožňuje kontrolovat, upravovat nebo přizpůsobit proces odesílání. Tato ukázka se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> zaměřuje na vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.  
  
## <a name="the-iinstanceprovider"></a>Zprostředkovatel iinstance  
 V WCF dispečer vytvoří instance třídy <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>služby pomocí <xref:System.ServiceModel.Dispatcher.IInstanceProvider> , který implementuje rozhraní. Toto rozhraní má tři metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Když přijde zpráva Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> k vytvoření instance třídy služby ke zpracování zprávy. Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall> nastavena na novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je vytvořen pro zpracování každé zprávy, která dorazí, tak se nazývá vždy, když zpráva dorazí.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je shodné s předchozí metodou, s výjimkou tohoto je vyvolána, pokud neexistuje žádný Message argument.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po uplynutí životnosti instance služby dispečer <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> volá metodu. Stejně jako <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> pro metodu, frekvence volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je určena vlastnost.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadované objektsdrálky sémantiku pro službu. Proto tato ukázka `ObjectPoolingInstanceProvider` má typ, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> který poskytuje vlastní implementaci pro sdružování. Při `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, namísto vytvoření nové instance, vlastní implementace hledá existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V opačném případě je vytvořen nový objekt. Implementace pro `GetInstance` je uveden v následujícím ukázkovém kódu.  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpět do `ActiveObjectsCount` fondu a sníží hodnotu. Můžete `Dispatcher` volat tyto metody z různých vláken, a proto je vyžadován `ObjectPoolingInstanceProvider` synchronizovaný přístup k členům na úrovni třídy ve třídě.  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 Metoda `ReleaseInstance` poskytuje funkci "vyčištění inicializace". Obvykle fond udržuje minimální počet objektů po dobu životnosti fondu. Však může být období nadměrného využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Nakonec při fondu stane méně aktivní, tyto nadbytečné objekty se může stát další režii. Proto když `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který aktivuje a provede cyklus čištění.  
  
## <a name="adding-the-behavior"></a>Přidání chování  
 Rozšíření vrstvy dispečera jsou zahnutý nahoru pomocí následující chod:  
  
- Chování služby. Ty umožňují přizpůsobení celého běhu služby.  
  
- Chování koncového bodu. Ty umožňují přizpůsobení koncových bodů služby, konkrétně dispečera kanálu a koncového bodu.  
  
- Chování smlouvy. Ty umožňují přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> tříd a tříd na straně klienta a služby v uvedeném pořadí.  
  
 Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby. Chování služby jsou vytvořeny <xref:System.ServiceModel.Description.IServiceBehavior> implementací rozhraní. Existuje několik způsobů, jak seznámit model služby o vlastní chování:  
  
- Použití vlastního atributu.  
  
- Imperativně přidání do kolekce chování popis služby.  
  
- Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořen zkoumá atributy použité v definici typu služby a přidá dostupné chování do kolekce chování popis služby.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>tři <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>metody <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>-- , a . Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> se používá k zajištění, že chování lze použít na službu. V této ukázce implementace zajišťuje, že <xref:System.ServiceModel.InstanceContextMode.Single>služba není nakonfigurována s . Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> se používá ke konfiguraci vazby služby. Není vyžadováno v tomto scénáři. Slouží <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> ke konfiguraci dispečerů služby. Tato metoda je volána <xref:System.ServiceModel.ServiceHost> WCF při inicializování. Do této metody jsou předány následující parametry:  
  
- `Description`: Tento argument poskytuje popis služby pro celou službu. To lze použít ke kontrole popisdat o koncových bodech služby, smlouvy, vazby a další data.  
  
- `ServiceHostBase`: Tento argument <xref:System.ServiceModel.ServiceHostBase> poskytuje, který je právě inicializován.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementaci `ObjectPoolingInstanceProvider` je vytvořena instance a přiřazena <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> k vlastnosti v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v ServiceHostBase.  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída několik členů pro přizpůsobení fondu objektů pomocí argumentů atributu. Mezi tyto <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>členy <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>patří , , a , aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.  
  
 Chování sdružování objektů lze nyní přidat do služby WCF anotací `ObjectPooling` implementace služby s nově vytvořeným vlastním atributem.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázka ukazuje výhody výkonu, které lze získat pomocí sdružování objektů v určitých scénářích.  
  
 Aplikace služby implementuje `WorkService` `ObjectPooledWorkService`dvě služby – a . Obě služby sdílejí stejnou implementaci – obě vyžadují `DoWork()` nákladnou inicializaci a pak zveřejňují metodu, která je relativně levná. Jediným rozdílem `ObjectPooledWorkService` je, že má sdružování objektů nakonfigurováno:  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 Při spuštění klienta, to `WorkService` krát volání 5 krát. To pak krát `ObjectPooledWorkService` volání 5 krát. Poté se zobrazí časový rozdíl:  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> Při prvním spuštění klienta se zdá, že obě služby mají přibližně stejnou dobu. Pokud znovu spustíte ukázku, uvidíte, že `ObjectPooledWorkService` vrátí mnohem rychleji, protože instance tohoto objektu již existuje ve fondu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
