---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 82b81637deb0715d19109794348d2a2bcda7f0d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594618"
---
# <a name="pooling"></a>Sdružování
Tato ukázka předvádí, jak můžete Windows Communication Foundation (WCF) pro podporu sdružování objektů. Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobný `ObjectPoolingAttribute` funkci atributu Enterprise Services. Sdružování objektů může poskytovat výrazné zvýšení výkonu aplikace. Může ale mít opačný efekt, pokud se nepoužívá správně. Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytváření často používaných objektů, které vyžadují rozsáhlou inicializaci. Nicméně pokud volání metody u objektu ve fondu trvá značnou dobu, sdružování objektů zařadí do fronty další požadavky hned po dosažení maximální velikosti fondu. Proto může neúspěšné obsluhovat některé žádosti o vytvoření objektu vyvoláním výjimky časového limitu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Prvním krokem při vytváření rozšíření WCF je určení bodu rozšiřitelnosti, který se má použít.  
  
 V rámci WCF pojem *Dispatcher* označuje komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod v rámci služby uživatele a pro převod návratových hodnot z této metody na odchozí zprávu. Služba WCF vytvoří dispečera pro každý koncový bod. Klient WCF musí použít dispečera, pokud je kontrakt přidružený k tomuto klientovi duplexní smlouvou.  
  
 Odesílatelé kanálu a koncových bodů nabízejí rozšiřitelnost kanálu a smlouvy tím, že zveřejňují různé vlastnosti, které řídí chování dispečera. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A>Vlastnost také umožňuje kontrolu, úpravu nebo přizpůsobení procesu odesílání. Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 Ve službě WCF vytvoří dispečer instance třídy služby pomocí <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> , který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní. Toto rozhraní má tři metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Když zpráva dorazí dispečera, volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodu pro vytvoření instance třídy služby ke zpracování zprávy. Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností. Například pokud je <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> novou instanci třídy služby, je vytvořena pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> se zavolá při každém přijetí zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Jedná se o shodu s předchozí metodou, s výjimkou toho, že je vyvolána, pokud neexistuje žádný argument zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Pokud uplynula doba života instance služby, Dispečer volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metodu. Stejně jako u <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody je frekvence volání této metody určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje pro službu nezbytnou sémantiku sdružování objektů. Proto má tato ukázka `ObjectPoolingInstanceProvider` typ, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování. Při `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody místo vytvoření nové instance vyhledá vlastní implementace existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V opačném případě se vytvoří nový objekt. Implementace pro `GetInstance` je uvedena v následujícím ukázkovém kódu.  
  
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
  
 Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpátky do fondu a sníží `ActiveObjectsCount` hodnotu. Rozhraní `Dispatcher` může volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup ke členům úrovně třídy ve `ObjectPoolingInstanceProvider` třídě.  
  
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
  
 `ReleaseInstance`Metoda poskytuje funkci Vyčištění inicializace. Fond běžně udržuje minimální počet objektů za dobu života fondu. Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci. Pokud se ale fond stane méně aktivním, může se stát, že tyto nadbytečné objekty budou dodatečně režijní. Proto když se `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který spustí a provede čisticí cyklus.  
  
## <a name="adding-the-behavior"></a>Přidání chování  
 Rozšíření dispečera vrstev jsou zapojená pomocí následujícího chování:  
  
- Chování služby. Tyto možnosti umožňují přizpůsobení celého modulu runtime služby.  
  
- Chování koncového bodu. To umožňuje přizpůsobení koncových bodů služby, konkrétně kanálu a dispečera koncového bodu.  
  
- Chování kontraktu. Tyto možnosti umožňují přizpůsobení obou tříd i <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> na straně klienta i služby.  
  
 Pro účely rozšíření sdružování objektů musí být vytvořeno chování služby. Chování služby je vytvořeno implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní. Existuje několik způsobů, jak zajistit, aby Service Model věděli o vlastním chování:  
  
- Použití vlastního atributu.  
  
- Imperativně přidejte do kolekce chování popisu služby.  
  
- Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořen, prochází atributy používané v definici typu služby a přidává dostupné chování do kolekce chování popisu služby.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má v něm tři metody, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> . <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>Metoda se používá k zajištění toho, aby bylo možné chování použít na službu. V této ukázce implementace zajišťuje, aby služba nebyla nakonfigurovaná pomocí <xref:System.ServiceModel.InstanceContextMode.Single> . <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>Metoda se používá ke konfiguraci vazeb služby. V tomto scénáři to není vyžadováno. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>Slouží ke konfiguraci expedičních odpravcích služby. Tato metoda je volána službou WCF při <xref:System.ServiceModel.ServiceHost> inicializaci. Do této metody jsou předány následující parametry:  
  
- `Description`: Tento argument poskytuje popis služby pro celou službu. Tato možnost slouží k prověření popisných dat o koncových bodech, kontraktech, vazbách a dalších datech služby.  
  
- `ServiceHostBase`: Tento argument poskytuje <xref:System.ServiceModel.ServiceHostBase> aktuálně inicializovaný.  
  
 V vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementaci `ObjectPoolingInstanceProvider` je vytvořena instance nové instance a přiřazena k <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnosti v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> z objektu ServiceHostBase.  
  
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má <xref:System.EnterpriseServices.ObjectPoolingAttribute> Třída více členů k přizpůsobení fondu objektů pomocí argumentů atributu. Mezi tyto členy patří <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> , <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> , a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A> , aby odpovídaly sadě funkcí sdružování objektů poskytované službami .NET Enterprise Services.  
  
 Chování sdružování objektů se teď dá přidat ke službě WCF tím, že se pokládá na implementaci služby s nově vytvořeným vlastním `ObjectPooling` atributem.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázka předvádí výhody výkonu, které lze v určitých scénářích využít při vytváření fondů objektů.  
  
 Aplikace služby implementuje dvě služby – `WorkService` a `ObjectPooledWorkService` . Obě služby sdílejí stejnou implementaci – oba vyžadují nákladný inicializaci a pak zveřejňují `DoWork()` metodu, která je poměrně levné. Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:  
  
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
> Při prvním spuštění klienta se obě služby projeví přibližně po stejnou dobu. Pokud ukázku znovu spustíte, vidíte, že `ObjectPooledWorkService` výsledek vrátí mnohem rychlejší, protože ve fondu již existuje instance daného objektu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!NOTE]
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
