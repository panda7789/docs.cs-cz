---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183599"
---
# <a name="instancing-initialization"></a>Inicializace vytváření instancí
Tato ukázka rozšiřuje [sdružování](../../../../docs/framework/wcf/samples/pooling.md) vzorku `IObjectControl`definováním rozhraní , který přizpůsobí inicializaci objektu aktivací a deaktivací. Klient vyvolá metody, které vrátí objekt do fondu a které nevrátí objekt do fondu.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="extensibility-points"></a>Body rozšiřitelnosti  
 Prvním krokem při vytváření rozšíření Windows Communication Foundation (WCF) je rozhodnout o bodu rozšiřitelnosti použít. V WCF termín *EndpointDispatcher* odkazuje na součást za běhu, která je zodpovědná za převod příchozích zpráv na vyvolání metody ve službě uživatele a za převod vrácených hodnot z této metody na odchozí zprávu. Služba WCF vytvoří endpointdispatcher pro každý koncový bod.  
  
 EndpointDispatcher nabízí obor koncového bodu (pro všechny zprávy přijaté nebo odeslané službou) rozšiřitelnost pomocí třídy. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Tato třída umožňuje přizpůsobit různé vlastnosti, které řídí chování EndpointDispatcher. Tato ukázka se <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> zaměřuje na vlastnost, která odkazuje na objekt, který poskytuje instance třídy služby.  
  
## <a name="iinstanceprovider"></a>Iinstanceprovider  
 V WCF EndpointDispatcher vytvoří instance třídy služby pomocí zprostředkovatele <xref:System.ServiceModel.Dispatcher.IInstanceProvider> instance, který implementuje rozhraní. Toto rozhraní má pouze dvě metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Když přijde zpráva, Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> k vytvoření instance třídy služby ke zpracování zprávy. Frekvence volání této metody je určena <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>nastavena na , je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, tak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> se nazývá vždy, když přijde zpráva.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Když instance služby dokončí zpracování zprávy, EndpointDispatcher volá metodu. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> Stejně <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> jako v metodě je frekvence volání této <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> metody určena vlastností.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Třída `ObjectPoolInstanceProvider` obsahuje implementaci pro fond objektů. Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstvou modelu služby. Když EndpointDispatcher volá <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu namísto vytvoření nové instance, vlastní implementace hledá existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V `ObjectPoolInstanceProvider` opačném případě `ActiveObjectsCount` zkontroluje, zda vlastnost (počet objektů vrácených z fondu) dosáhla maximální velikost fondu. Pokud tomu tak není, je vytvořena nová `ActiveObjectsCount` instance a vrácena volajícímu a následně se zpřímí. V opačném případě je požadavek na vytvoření objektu zařazen do fronty po nakonfigurovanou dobu. Implementace pro `GetObjectFromThePool` je uveden v následujícím ukázkovém kódu.  
  
```csharp
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
  
 Vlastní `ReleaseInstance` implementace přidá uvolněnou instanci zpět do `ActiveObjectsCount` fondu a sníží hodnotu. EndpointDispatcher můžete volat tyto metody z různých vláken, a proto je `ObjectPoolInstanceProvider` vyžadován synchronizovaný přístup k členům na úrovni třídy ve třídě.  
  
```csharp
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
  
 Metoda `ReleaseInstance` poskytuje funkci *vyčištění inicializace.* Obvykle fond udržuje minimální počet objektů po dobu životnosti fondu. Však může být období nadměrného využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Nakonec při fondu se stane méně aktivní tyto nadbytečné objekty se může stát další režii. Proto při `activeObjectsCount` dosažení nuly je spuštěn časovač nečinnosti, který aktivuje a provede cyklus čištění.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 Rozšíření vrstev ServiceModel jsou zahnutý nahoru pomocí následujících chování:  
  
- Chování služby: Umožňují přizpůsobení celého běhu služby.  
  
- Chování koncového bodu: Umožňují přizpůsobení konkrétního koncového bodu služby, včetně endpointdispatcheru.  
  
- Chování smlouvy: Umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy na straně klienta nebo služby v uvedeném pořadí.  
  
- Chování operace: Umožňují přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy na straně klienta nebo služby v uvedeném pořadí.  
  
 Pro účely rozšíření sdružování objektů lze vytvořit chování koncového bodu nebo chování služby. V tomto příkladu používáme chování služby, které platí schopnost sdružování objektů pro každý koncový bod služby. Chování služby jsou vytvořeny <xref:System.ServiceModel.Description.IServiceBehavior> implementací rozhraní. Existuje několik způsobů, jak seznámit ServiceModel vlastní chování:  
  
- Použití vlastního atributu.  
  
- Imperativně přidání do kolekce chování popis služby.  
  
- Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořen, zkontroluje atributy použité v definici typu služby a přidá dostupné chování do kolekce chování popis služby.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` metody: a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Tyto metody jsou volány <xref:System.ServiceModel.ServiceHost> WCF při inicializování. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>nazývá jako první; umožňuje, aby služba byla zkontrolována na nekonzistenci. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>nazývá další; Tato metoda je vyžadována pouze ve velmi pokročilých scénářích. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>je volána jako poslední a je zodpovědná za konfiguraci běhu. Následující parametry jsou <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>předány do :  
  
- `Description`: Tento parametr poskytuje popis služby pro celou službu. To lze použít ke kontrole popisdat o koncových bodech služby, smlouvy, vazby a další data spojená se službou.  
  
- `ServiceHostBase`: Tento parametr <xref:System.ServiceModel.ServiceHostBase> poskytuje aktuálně inicializován.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> `ObjectPoolInstanceProvider` implementaci je vytvořena instance instance a přiřazena <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> vlastnosti v každé, která je připojena k <xref:System.ServiceModel.ServiceHostBase>.  
  
```csharp
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má `ObjectPoolingAttribute` třída několik členů pro přizpůsobení fondu objektů pomocí argumentů atributu. Mezi tyto `MaxSize` `MinSize`členy `Enabled` `CreationTimeout`patří , , a , aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.  
  
 Chování sdružování objektů lze nyní přidat do služby WCF anotací `ObjectPooling` implementace služby s nově vytvořeným vlastním atributem.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Aktivace a deaktivace hákování  
 Primárním cílem sdružování objektů je optimalizace krátkodobých objektů s relativně nákladným vytvářením a inicializací. Proto může poskytnout dramatický výkon zvýšení aplikace, pokud správně používá. Vzhledem k tomu, že objekt je vrácena z fondu, konstruktor se nazývá pouze jednou. Některé aplikace však vyžadují určitou úroveň řízení, aby mohly inicializovat a vyčistit prostředky používané během jednoho kontextu. Například objekt používaný pro sadu výpočtů může obnovit svá soukromá pole před zpracováním dalšího výpočtu. Enterprise Services povolila tento druh inicializace specifické `Activate` pro `Deactivate` kontext <xref:System.EnterpriseServices.ServicedComponent> tím, že umožňuje vývojářobjektu přepsat a metody ze základní třídy.  
  
 Fond objektů volá `Activate` metodu těsně před vrácením objektu z fondu. `Deactivate`je volána, když se objekt vrátí zpět do fondu. Základní <xref:System.EnterpriseServices.ServicedComponent> třída má `boolean` také `CanBePooled`vlastnost s názvem , která slouží k upozornění fondu, zda objekt může být dále sdružený.  
  
 Chcete-li napodobení této funkce,`IObjectControl`ukázka deklaruje veřejné rozhraní ( ), který má výše uvedené členy. Toto rozhraní je pak implementováno třídami služeb určenými k poskytování inicializace specifické pro kontext. Implementace <xref:System.ServiceModel.Dispatcher.IInstanceProvider> musí být upravena tak, aby splňovala tyto požadavky. Nyní pokaždé, když získáte objekt `GetInstance` voláním metody, je nutné `IObjectControl.` zkontrolovat, zda objekt implementuje Pokud ano, musíte správně volat metodu. `Activate`  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Při vrácení objektu do fondu je vyžadována `CanBePooled` kontrola pro vlastnost před přidáním objektu zpět do fondu.  
  
```csharp  
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
  
 Vzhledem k tomu, že vývojář služby může rozhodnout, zda objekt může být sdružený, počet objektů ve fondu v daném čase může přejít pod minimální velikost. Proto je nutné zkontrolovat, zda počet objektů klesla pod minimální úroveň a provést potřebnou inicializaci v procesu čištění.  
  
```csharp  
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
  
 Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole. Stisknutím klávesy Enter v každém okně konzoly vypněte službu a klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
