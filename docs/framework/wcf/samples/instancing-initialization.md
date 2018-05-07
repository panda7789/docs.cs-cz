---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 75b8d2a2696d5900fd7bffe42dbaf62b9f6ce694
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="instancing-initialization"></a>Inicializace vytváření instancí
Tato ukázka rozšiřuje [Pooling](../../../../docs/framework/wcf/samples/pooling.md) ukázku definováním rozhraní, `IObjectControl`, který přizpůsobí inicializace objektu aktivace a deaktivace ho. Klient volá metody, které vrací objekt do fondu a která nevrátí objektu do fondu.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="extensibility-points"></a>Body rozšiřitelnosti  
 Prvním krokem při vytváření rozšíření pro Windows Communication Foundation (WCF) je rozhodnout bodem rozšíření používat. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], termín *EndpointDispatcher* odkazuje na komponentu běhu odpovědný za převodu příchozí zprávy volání metod na uživatele služby a pro převod návratové hodnoty z dané metody pro odchozí zprávy. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba vytvoří EndpointDispatcher pro každý koncový bod.  
  
 EndpointDispatcher nabízí koncový bod oboru (pro všechny zprávy přijatých nebo odeslaných službou) rozšiřitelnost pomocí <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> třídy. Tato třída umožňuje přizpůsobit různé vlastnosti tohoto ovládání chování EndpointDispatcher. Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instancí třídy služby.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], EndpointDispatcher vytváří instance třídy služeb pomocí instance zprostředkovatele, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní. Toto rozhraní má jenom dvě metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Při doručení zprávy, volání dispečera <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu pro vytvoření instance třídy služeb, ke zpracování zprávy. Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, je vytvořit novou instanci třídy služeb pro zpracování jednotlivých zpráv, které dorazí, tak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána, když doručení zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Pokud je instance služby dokončí zpracování zprávy, EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda. Jako v <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody Četnost volání této metody je dáno <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.  
  
## <a name="the-object-pool"></a>Fond objektů  
 `ObjectPoolInstanceProvider` Třída obsahuje implementaci pro fond objektů. Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstva modelu služby. Při volání EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, místo vytvoření nové instance, vlastní implementaci vypadá pro existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V opačném `ObjectPoolInstanceProvider` kontroluje, zda `ActiveObjectsCount` vlastnost (počet objektů vrácených z fondu) byl dosažen maximální počet. Pokud ne, novou instanci se vytvoří a vrácen volajícímu a `ActiveObjectsCount` se následně zvýší. V opačném případě požadavek na vytvoření objektů je zařadit do fronty pro určenou dobu. Implementace pro `GetObjectFromThePool` je znázorněno v následujícím ukázkovém kódu.  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 Vlastní `ReleaseInstance` implementace přidá vydaná instance zpět do fondu a snižují se vždy `ActiveObjectsCount` hodnotu. EndpointDispatcher tyto metody můžete volat z různých vláknech a proto synchronizované přístupu na úrovni členy třídy v `ObjectPoolInstanceProvider` je vyžadován.  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 `ReleaseInstance` Poskytuje metody *vyčištění inicializace* funkce. Za normálních okolností fond udržuje minimální počet objektů po dobu jeho existence fondu. Však může být období nadměrné využití, které vyžadují vytváření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Když se změní na míň aktivní fondu tyto nadbytečné objekty může přestat zvýšené režii. Proto když `activeObjectsCount` hodnota nula nečinnosti časovače spuštění, který aktivuje vyčištění cyklus.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozšíření vrstvy ServiceModel se připojili pomocí následující chování:  
  
-   Chování služby:, Tyto rutiny umožňují k přizpůsobení modulu runtime celé služby.  
  
-   Chování koncový bod:, Tyto rutiny umožňují pro přizpůsobení koncový bod konkrétní službu, včetně EndpointDispatcher.  
  
-   Chování kontraktu: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na klienta nebo služby v uvedeném pořadí.  
  
-   Operace chování: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy na klienta nebo služby v uvedeném pořadí.  
  
 Pro účely objekt sdružování rozšíření mohou být vytvořeny chování koncového bodu nebo chování služby. V tomto příkladu používáme chování služby, která se vztahuje objekt sdružování schopnost každý koncový bod služby. Chování služby jsou vytvořené pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní. Chcete-li vědět, že vlastní chování ServiceModel několika způsoby:  
  
-   Pomocí vlastních atributů.  
  
-   Imperativní přidáním do kolekce chování popis služby.  
  
-   Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořená, prozkoumá atributy používané v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Rozhraní má tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Tyto metody jsou volány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] při <xref:System.ServiceModel.ServiceHost> inicializace. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> jako první; To umožňuje službu, kterou chcete být prověřovány za účelem nalezení nekonzistencí. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> je volána vedle; Tato metoda je potřeba jenom v velmi pokročilých scénářích. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> Označuje se poslední a je zodpovědná za konfiguraci modulu runtime. Tyto parametry se předávají do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Tento parametr obsahuje popis služby pro celé služby. To slouží ke kontrole popis data o koncové body služby, kontrakty, vazby a další data spojené s touto službou.  
  
-   `ServiceHostBase`: Poskytuje tento parametr <xref:System.ServiceModel.ServiceHostBase> která aktuálně probíhá inicializace.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace, novou instanci třídy `ObjectPoolInstanceProvider` se vytvořit instanci a přiřadí do <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každé <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> připojená k <xref:System.ServiceModel.ServiceHostBase>.  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace `ObjectPoolingAttribute` třída obsahuje několik členů k přizpůsobení fondu objektů pomocí argumenty atributu. Zahrnout tito členové `MaxSize`, `MinSize`, `Enabled` a `CreationTimeout`, tak, aby odpovídaly objekt sdružování sada funkcí poskytovaných služeb .NET Enterprise.  
  
 Objekt sdružování chování teď jde přidat do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby podle zadávání poznámek k implementaci služby s nově vytvořené vlastní `ObjectPooling` atribut.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Zapojování aktivace a deaktivace  
 Primární cílem sdružování objektů je za účelem optimalizace krátkodobou objekty s relativně nákladné vytváření a inicializace. Proto je zvýšení výrazné výkonu přidělit aplikaci pokud správně používá. Vzhledem k tomu, že objekt se vrátí z fondu, je konstruktoru volat pouze jednou. Ale některé aplikace vyžadují některé úroveň kontroly tak, aby můžou inicializaci a čištění prostředky využívané během jednotlivý kontext. Například objekt používá pro sadu výpočty můžete resetovat jeho privátním polím před zpracováním další výpočtu. Tento druh inicializace konkrétní povolit služby Enterprise tím, že vývojář objekt přepsat `Activate` a `Deactivate` metody z <xref:System.EnterpriseServices.ServicedComponent> základní třídy.  
  
 Volání objektu fondu `Activate` metoda těsně před vrácením objekt z fondu. `Deactivate` je volána, když objekt vrátí zpět do fondu. <xref:System.EnterpriseServices.ServicedComponent> Základní třída má také `boolean` vlastnost s názvem `CanBePooled`, který slouží k upozornění fondu, zda objekt může být ve fondu další.  
  
 Tak, aby napodoboval tuto funkci, ukázky deklaruje veřejné rozhraní (`IObjectControl`) s zmíněnými členy. Toto rozhraní je implementováno pak službou třídy určené k poskytnutí konkrétní Inicializace kontextu. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementace musí upravit, aby tyto požadavky splňují. Nyní, pokaždé, když jste získat objekt voláním `GetInstance` metoda, je nutné zkontrolovat, zda objekt implementuje `IObjectControl.` Pokud ano, musí volat `Activate` metoda správně.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Když se vrátí objekt do fondu, je vyžadována pro kontrolu `CanBePooled` vlastnost před přidáním objektu zpět do fondu.  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 Protože vývojáři služby můžete rozhodnout, zda objekt můžete ve fondu, můžete přejít počet objektů ve fondu v daném okamžiku nižší než minimální velikost. Proto musíte zkontrolovat, zda počet objektů přešel nižší než minimální úroveň a provést potřebné inicializaci v postupu čištění.  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy Enter v každé okna konzoly vypnout klienta a služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>Viz také
