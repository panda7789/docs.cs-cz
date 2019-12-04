---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: d2962004376cf6f0752067d4e03828cd894efd01
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716519"
---
# <a name="pooling"></a>Sdružování
Tato ukázka předvádí, jak můžete Windows Communication Foundation (WCF) pro podporu sdružování objektů. Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobný funkci `ObjectPoolingAttribute` atributů podnikových služeb. Sdružování objektů může poskytovat výrazné zvýšení výkonu aplikace. Může ale mít opačný efekt, pokud se nepoužívá správně. Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytváření často používaných objektů, které vyžadují rozsáhlou inicializaci. Nicméně pokud volání metody u objektu ve fondu trvá značnou dobu, sdružování objektů zařadí do fronty další požadavky hned po dosažení maximální velikosti fondu. Proto může neúspěšné obsluhovat některé žádosti o vytvoření objektu vyvoláním výjimky časového limitu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Prvním krokem při vytváření rozšíření WCF je určení bodu rozšiřitelnosti, který se má použít.  
  
 V rámci WCF pojem *Dispatcher* označuje komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod v rámci služby uživatele a pro převod návratových hodnot z této metody na odchozí zprávu. Služba WCF vytvoří dispečera pro každý koncový bod. Klient WCF musí použít dispečera, pokud je kontrakt přidružený k tomuto klientovi duplexní smlouvou.  
  
 Odesílatelé kanálu a koncových bodů nabízejí rozšiřitelnost kanálu a smlouvy tím, že zveřejňují různé vlastnosti, které řídí chování dispečera. Vlastnost <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> také umožňuje kontrolu, úpravu nebo přizpůsobení procesu odesílání. Tato ukázka se zaměřuje na vlastnost <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, která odkazuje na objekt, který poskytuje instance třídy služby.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 Ve službě WCF vytvoří dispečer instance třídy služby pomocí <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, který implementuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Toto rozhraní má tři metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: po doručení zprávy Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> k vytvoření instance třídy služby pro zpracování zprávy. Frekvence volání této metody je určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Pokud je například vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> nastavena na hodnotu <xref:System.ServiceModel.InstanceContextMode.PerCall> je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána při doručení zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jedná se o shodu s předchozí metodou, s výjimkou toho, že je vyvolána, pokud neexistuje žádný argument zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: když uplyne doba života instance služby, Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>. Stejně jako u metody <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je frekvence volání této metody určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Vlastní implementace <xref:System.ServiceModel.Dispatcher.IInstanceProvider> poskytuje pro službu nezbytnou sémantiku sdružování objektů. Proto má tato ukázka typ `ObjectPoolingInstanceProvider`, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování. Pokud `Dispatcher` volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> namísto vytvoření nové instance, vlastní implementace vyhledá existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V opačném případě se vytvoří nový objekt. Implementace pro `GetInstance` je uvedena v následujícím ukázkovém kódu.  
  
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
  
 Vlastní implementace `ReleaseInstance` přidá uvolněnou instanci zpátky do fondu a sníží hodnotu `ActiveObjectsCount`. `Dispatcher` mohou volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup ke členům úrovně třídy ve třídě `ObjectPoolingInstanceProvider`.  
  
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
  
 Metoda `ReleaseInstance` poskytuje funkci vyčištění při inicializaci. Fond běžně udržuje minimální počet objektů za dobu života fondu. Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci. Pokud se ale fond stane méně aktivním, může se stát, že tyto nadbytečné objekty budou dodatečně režijní. Proto když `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který spustí a provede čisticí cyklus.  
  
## <a name="adding-the-behavior"></a>Přidání chování  
 Rozšíření dispečera vrstev jsou zapojená pomocí následujícího chování:  
  
- Chování služby. Tyto možnosti umožňují přizpůsobení celého modulu runtime služby.  
  
- Chování koncového bodu. To umožňuje přizpůsobení koncových bodů služby, konkrétně kanálu a dispečera koncového bodu.  
  
- Chování kontraktu. Tato možnost umožňuje přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy v klientovi i v uvedeném pořadí.  
  
 Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby. Chování služby se vytváří implementací rozhraní <xref:System.ServiceModel.Description.IServiceBehavior>. Existuje několik způsobů, jak zajistit, aby Service Model věděli o vlastním chování:  
  
- Použití vlastního atributu.  
  
- Imperativně přidejte do kolekce chování popisu služby.  
  
- Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když je vytvořen <xref:System.ServiceModel.ServiceHost>, prověřuje atributy používané v definici typu služby a přidá k němu dostupné chování do kolekce chování popisu služby.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm tři metody--<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Metoda <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> slouží k zajištění toho, aby bylo možné chování použít na službu. V této ukázce implementace zajišťuje, že služba není nakonfigurovaná s <xref:System.ServiceModel.InstanceContextMode.Single>. Metoda <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> slouží ke konfiguraci vazeb služby. V tomto scénáři to není vyžadováno. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> slouží ke konfiguraci expedičních odpravcích služby. Tato metoda je volána službou WCF při inicializaci <xref:System.ServiceModel.ServiceHost>. Do této metody jsou předány následující parametry:  
  
- `Description`: Tento argument poskytuje popis služby pro celou službu. Tato možnost slouží k prověření popisných dat o koncových bodech, kontraktech, vazbách a dalších datech služby.  
  
- `ServiceHostBase`: Tento argument poskytuje <xref:System.ServiceModel.ServiceHostBase>, který se právě inicializuje.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace nové instance `ObjectPoolingInstanceProvider` je vytvořena instance a přiřazena vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> v každém <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v objektu ServiceHostBase.  
  
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má <xref:System.EnterpriseServices.ObjectPoolingAttribute> třídy několik členů k přizpůsobení fondu objektů pomocí argumentů atributu. Mezi tyto členy patří <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.  
  
 Chování sdružování objektů lze nyní přidat do služby WCF zadáním poznámky k implementaci služby pomocí nově vytvořeného vlastního atributu `ObjectPooling`.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázka předvádí výhody výkonu, které lze v určitých scénářích využít při vytváření fondů objektů.  
  
 Aplikace služby implementuje dvě služby – `WorkService` a `ObjectPooledWorkService`. Obě služby sdílejí stejnou implementaci – obě služby vyžadují nákladný inicializaci a pak zveřejňují `DoWork()`é metody, které jsou poměrně levné. Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:  
  
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
  
 Když spustíte klienta nástroje, čas zavolá `WorkService` 5 časů. Pak časy, které volají `ObjectPooledWorkService` 5 časů. Rozdíl v čase se pak zobrazí:  
  
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
> Při prvním spuštění klienta se obě služby projeví přibližně po stejnou dobu. Pokud ukázku znovu spustíte, vidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože ve fondu již existuje instance daného objektu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
