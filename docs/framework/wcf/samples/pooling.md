---
title: "Sdružování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7e893a48e590f2b8a2ada88662cf454dc7881e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pooling"></a>Sdružování
Tento příklad ukazuje, jak rozšířit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro podporu sdružování objektů. Ukázka ukazuje, jak vytvořit atribut, který je syntakticky a sémanticky podobná `ObjectPoolingAttribute` atribut funkce služby Enterprise. Sdružování objektů zajistí výrazné zvýšení výkonu aplikace na výkon. Pokud se nepoužívá správně však může mít opačný efekt. Sdružování objektů pomáhá snížit režii znovu vytvořit často používaných objektů, které vyžadují rozsáhlé inicializace. Však sdružování objekt fronty Pokud volání metody na objekt ve fondu používá značné množství času na dokončení, další požadavky při dosažení k maximální velikosti fondu. Proto může dojít k selhání obsluze některé objekt požadavky na vytvoření byla vrácena výjimka časového limitu.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Prvním krokem při vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšíření je rozhodnutí o bodem rozšíření používat.  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] termín *dispečera* odkazuje na komponentu běhu odpovědný za převodu příchozí zprávy volání metod na uživatele služby a pro převod návratové hodnoty z dané metody na odchozí zpráva. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba vytvoří dispečera pro každý koncový bod. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, pokud smlouvy přidružené tohoto klienta je duplexního kontraktu, musíte používat dispečera.  
  
 Kanál a koncový bod dispečerů nabízejí kanál- a rozšiřitelnost v rámci smlouvy díky zpřístupnění různé vlastnosti, které řídí chování dispečera. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Vlastnost můžete také zkontrolovat, upravit nebo přizpůsobit odesílající proces. Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instancí třídy služby.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], dispečera vytváří instance třídy pomocí služby <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní. Toto rozhraní obsahuje tři metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Při doručení zprávy dispečera volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metodu pro vytvoření instance třídy služeb, ke zpracování zprávy. Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall> pro zpracování jednotlivých zpráv, které dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> je volána, když doručení zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Toto je stejný jako předchozí metoda, s výjimkou to je volána, když je argument žádné zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Pokud dojde k uplynutí doby platnosti instance služby, volání dispečera <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> metoda. Stejně jako pro <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Vlastní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementace poskytuje požadovaný objekt sdružování sémantiku pro službu. Proto tato ukázka má `ObjectPoolingInstanceProvider` typ, který poskytuje vlastní implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro sdružování. Když `Dispatcher` volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> metody, místo vytvoření nové instance, vlastní implementaci vypadá pro existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. Jinak se vytvoří nový objekt. Implementace pro `GetInstance` je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Vlastní `ReleaseInstance` implementace přidá vydaná instance zpět do fondu a snižují se vždy `ActiveObjectsCount` hodnotu. `Dispatcher` Tyto metody můžete volat z různých vláknech a proto synchronizované přístupu na úrovni členy třídy v `ObjectPoolingInstanceProvider` je vyžadován.  
  
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
  
 `ReleaseInstance` Metoda nabízí funkci "Vyčištění inicializace". Za normálních okolností fond udržuje minimální počet objektů po dobu jeho existence fondu. Však může být období nadměrné využití, které vyžadují vytváření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Nakonec když se stane fondu míň aktivní, tyto nadbytečné objekty se může stát zvýšené režii. Proto když `activeObjectsCount` dosáhnou nula, nečinnosti časovače je spuštěno, který aktivuje vyčištění cyklus.  
  
## <a name="adding-the-behavior"></a>Přidání chování  
 Rozšíření dispečerů vrstvy se připojili pomocí následující chování:  
  
-   Chování služby. Tyto rutiny umožňují k přizpůsobení modulu runtime celé služby.  
  
-   Koncový bod chování. Tyto rutiny umožňují pro vlastní nastavení koncových bodů služby, konkrétně kanál a koncový bod dispečera.  
  
-   Kontrakt chování. Tyto rutiny umožňují pro přizpůsobení obou <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta a služby v uvedeném pořadí.  
  
 Pro účely objekt sdružování rozšíření musí být vytvořeny chování služby. Chování služby jsou vytvořené pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní. Chcete-li vědět, že vlastní chování modelu služby několika způsoby:  
  
-   Pomocí vlastních atributů.  
  
-   Imperativní přidáním do kolekce chování popis služby.  
  
-   Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> sestavený prověří atributy používané v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři metody v ní – <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Metoda se používá k zajištění, že chování může být použitá ke službě. V této ukázce implementace zajistí, že služba není nakonfigurována s <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Metoda slouží ke konfiguraci vazby služby. V tomto scénáři není potřeba. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Slouží ke konfiguraci služby dispečerů. Tato metoda je volána [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] při <xref:System.ServiceModel.ServiceHost> inicializace. Tyto parametry se předávají do této metody:  
  
-   `Description`: Tento argument obsahuje popis služby pro celé služby. To slouží ke kontrole popis data o koncové body služby, kontrakty, vazby a další data.  
  
-   `ServiceHostBase`: Poskytuje tento argument <xref:System.ServiceModel.ServiceHostBase> která aktuálně probíhá inicializace.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace novou instanci služby `ObjectPoolingInstanceProvider` se vytvořit instanci a přiřadí do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každé <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v ServiceHostBase.  
  
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace <xref:System.EnterpriseServices.ObjectPoolingAttribute> třída obsahuje několik členů k přizpůsobení fondu objektů pomocí argumenty atributu. Zahrnout tito členové <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, a <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, tak, aby odpovídaly objekt sdružování sada funkcí poskytovaných služeb .NET Enterprise.  
  
 Objekt sdružování chování teď jde přidat do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby podle zadávání poznámek k implementaci služby s nově vytvořené vlastní `ObjectPooling` atribut.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázka ukazuje výkon výhody, které můžete získaných pomocí sdružování objektů v některých scénářích.  
  
 Aplikace služby implementuje dvou služeb – `WorkService` a `ObjectPooledWorkService`. Jak služby sdílet stejnou implementaci – jejich jak vyžadovat nákladný inicializace a následně je zpřístupněte `DoWork()` metoda, která je relativně levný. Jediným rozdílem je, že `ObjectPooledWorkService` má nakonfigurované sdružování objektů:  
  
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
  
 Při spuštění klienta uplyne časový volání `WorkService` 5krát. Pak uplyne časový volání `ObjectPooledWorkService` 5krát. Rozdíl v čase se následně zobrazí:  
  
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
>  Při prvním spuštění klienta obě služby jsou trvat o stejnou dobu. Pokud znovu spustíte ukázku, můžete uvidíte, že `ObjectPooledWorkService` vrátí mnohem rychlejší, protože instance tohoto objektu již existuje ve fondu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a>Viz také
