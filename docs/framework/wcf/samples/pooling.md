---
title: Sdružování
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: f4df661ad5d831158da55fe3890805ccc5cd695f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307207"
---
# <a name="pooling"></a>Sdružování
Tato ukázka předvádí, jak rozšířit Windows Communication Foundation (WCF) pro podporu sdružování objektů. Vzorek ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobné `ObjectPoolingAttribute` atribut funkce podnikové služby. Sdružování objektů umožňují výrazné zvýšení výkonu aplikace. Pokud se nepoužívá správně však může mít opačný efekt. Sdružování objektů pomáhá snižovat režijní náklady na opětovné vytvoření často používané objekty, které vyžadují rozsáhlé inicializace. Nicméně pokud volání metody na objektu ve fondu trvá značné množství času k dokončení, sdružování objektů zařadí do fronty dalších žádostí ihned poté, co je dosaženo maximální velikosti fondu. Proto může dojít k selhání obsluhovat požadavky na vytvoření některý objekt vyvoláním výjimka časového limitu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Prvním krokem při vytváření rozšíření WCF je rozhodnout bodu rozšiřitelnosti pro použití.  
  
 Ve službě WCF termín *dispečer* odkazuje na komponentu za běhu pro převod příchozích zpráv do volání metod na uživatele služby a pro převod vrácené hodnoty z této metody na odchozí zprávu. Služba WCF vytvoří dispečer pro každý koncový bod. Pokud kontrakt přidružený tento klient je duplexního kontraktu, musíte použít klienta WCF dispečerem.  
  
 Nabízejí dispečerů kanálu a koncového bodu kanálu – a rozšiřitelnost smlouvy celou zveřejněním různé vlastnosti, které řídí chování dispečer. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Vlastnosti můžete také zkontrolovat, upravit nebo přizpůsobit dispatching proces. Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy service.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 Ve službě WCF, dispečer vytvoří instance třídy pomocí služeb <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, která implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní. Toto rozhraní obsahuje tři metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Při přijetí e-mailu dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodu pro vytvoření instance třídy službu ke zpracování zprávy. Četnost volání této metody se zakládá <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> zpracovat každou zprávu, která dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána při každém přijetí e-mailu.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je stejný jako předchozí metoda, s výjimkou toto se vyvolá, pokud neexistuje žádný argument zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Po uplynutí doby života instance služby, dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metody. Stejně jako u <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metoda, je určena Četnost volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadovaný objekt sdružování sémantiky pro službu. Proto tato ukázka má `ObjectPoolingInstanceProvider` typ, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování. Když `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, místo vytvoření nové instance, vlastní implementaci hledá existující objekt ve fondu v paměti. Pokud je k dispozici, bude vrácen. V opačném případě se vytvoří nový objekt. Implementace `GetInstance` je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Vlastní `ReleaseInstance` implementace přidá vydané instanci zpět do fondu a sníží `ActiveObjectsCount` hodnotu. `Dispatcher` Tyto metody lze volat z různých vláken a proto synchronizaci přístupu k členům třídy úrovni v `ObjectPoolingInstanceProvider` třída je povinné.  
  
```  
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
  
 `ReleaseInstance` Metoda obsahuje funkci "vyčistit inicializace". Fondu obvykle udržuje minimální počet objektů, které po dobu životnosti fondu. Může však být období nadměrnému využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Nakonec Jakmile fondu je méně aktivní, tyto objekty nadbytečné se může stát další režii. Proto, když `activeObjectsCount` dosáhne nulu, nečinnosti časovače, který se aktivuje a provede vyčištění cyklus spuštění.  
  
## <a name="adding-the-behavior"></a>Přidání chování  
 Rozšíření vrstvě dispečera se připojili pomocí následujícího chování:  
  
-   Chování služby. Tyto rutiny umožňují pro přizpůsobení celé služby modulu runtime.  
  
-   Chování koncového bodu. Tyto rutiny umožňují pro přizpůsobení koncových bodů služby, konkrétně kanálu a Dispečer koncového bodu.  
  
-   Chování kontraktu. Tyto rutiny umožňují pro přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta a služby v uvedeném pořadí.  
  
 Pro účely objekt sdružování rozšíření musí být vytvořeny chování služby. Chování služby jsou vytvořeny pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní. Existuje několik způsobů, jak vytvořit model služby používající vlastní chování:  
  
-   Pomocí vlastního atributu.  
  
-   Imperativně přidáním do kolekce chování popisu služby.  
  
-   Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořená prozkoumá atributy použité v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři metody v ní <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda se používá k zajištění, že chování lze použít ke službě. V této ukázce se implementace zajistí, že služba není nakonfigurována s <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda se používá ke konfiguraci vazby služby. V tomto scénáři není potřeba. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Slouží ke konfiguraci služby dispečerů. Tato metoda je volána službou WCF při <xref:System.ServiceModel.ServiceHost> je inicializována. Následující parametry jsou předány do této metody:  
  
-   `Description`: Tento argument obsahuje popis služby pro celou službu. To lze použít ke kontrole popis data o koncové body služby, kontrakty, vazby a další data.  
  
-   `ServiceHostBase`: Poskytuje tento argument <xref:System.ServiceModel.ServiceHostBase> , který je aktuálně inicializována.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace novou instanci sady `ObjectPoolingInstanceProvider` vytvořena a přiřazená <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každém <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v objektu ServiceHostBase.  
  
```  
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
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída má několik členů k přizpůsobení fondu objektů pomocí argumentů atributu. Zahrnout tyto členy <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, tak, aby odpovídaly objekt sdružování sadu funkcí poskytovanou služeb .NET Enterprise.  
  
 Objekt sdružování chování lze nyní přidat ke službě WCF anotací implementace služby nově vytvořené vlastním `ObjectPooling` atribut.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázce přinese zlepšení výkonu, které může být získaná použitím sdružování objektů v některých scénářích.  
  
 Aplikace služby implementuje dvou služeb – `WorkService` a `ObjectPooledWorkService`. Obě služby sdílet stejnou implementaci – jejich vyžadovat nákladná inicializace i pak vystavit `DoWork()` metod, které jsou relativně levné. Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:  
  
```  
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
  
 Když spustíte klienta, dojde k jejímu volání `WorkService` 5krát. Uplyne volání `ObjectPooledWorkService` 5krát. Rozdíl v čase se následně zobrazí:  
  
```  
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
>  Při prvním spuštění klienta obě služby se to trvat přibližně stejnou dobu. Pokud znovu spustíte ukázku, vidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože instance tohoto objektu již existuje ve fondu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
