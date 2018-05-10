---
title: Vlastní doba života
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="custom-lifetime"></a>Vlastní doba života
Tento příklad znázorňuje, jak napsat rozšíření Windows Communication Foundation (WCF) k poskytování služeb vlastní doba života pro sdílené instance služby WCF.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="shared-instancing"></a>Sdílené, vytváření instancí  
 WCF nabízí několik zřizování instancí režimy pro vaše instance služby. Režim vytváření instancí sdílené zahrnuté v tomto tématu poskytuje způsob, jak sdílet instanci služby mezi více typů komunikačních kanálů. Klienty můžete buď vyřešit instance adresa koncového bodu místně nebo se obraťte na metoda factory ve službě k získání adresa koncového bodu spuštěné instance. Jakmile má adresa koncového bodu, může vytvořit nový kanál a spustit komunikace. Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál ke stávající instanci služby.  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 Na rozdíl od jiných zřizování instancí režimy režimu sdílení zřizování instancí má jedinečný způsob vydání instance služby. Pokud pro instanci zavřeny všechny kanály, běh služby WCF spustí časovač. Pokud nikdo vytvoří připojení, než vyprší časový limit, WCF uvolní instanci a deklarace identity prostředky. Jako součást procesu rušením vyvolá WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda všech <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace před uvolněním instance. Pokud všechny z nich vrátí `true` vydání instance. V opačném případě <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědná za upozornění `Dispatcher` ze stavu nečinnosti pomocí metody zpětného volání.  
  
 Ve výchozím nastavení má hodnotu časového limitu nečinnosti <xref:System.ServiceModel.InstanceContext> je jedna minuta. Ale tento příklad znázorňuje, jak můžete rozšířit pomocí vlastního rozšíření.  
  
## <a name="extending-the-instancecontext"></a>Rozšíření objekt InstanceContext.  
 Ve službě WCF <xref:System.ServiceModel.InstanceContext> je propojení mezi instance služby a `Dispatcher`. WCF umožňuje rozšířit tuto součást modulu runtime přidáním nového stavu nebo chování pomocí jeho vzor extensible objektu. Vzor extensible objektu se používá v WCF buď rozšířit existující třídy runtime s novými funkcemi, nebo při přidání nových funkcí stavu do objektu. Existují tři rozhraní ve vzoru extensible objektu: `IExtensibleObject<T>`, `IExtension<T>`, a `IExtensionCollection<T>`.  
  
 `IExtensibleObject<T>` Rozhraní je implementováno modulem objekty, které chcete povolit rozšíření, které přizpůsobení jejich funkce.  
  
 `IExtension<T>` Rozhraní je implementováno modulem objekty, které může být rozšíření třídy typu `T`.  
  
 A nakonec `IExtensionCollection<T>` rozhraní je kolekce `IExtensions` umožňuje pro načítání `IExtensions` dle jejich typu.  
  
 Proto chcete-li rozšířit <xref:System.ServiceModel.InstanceContext> musí implementovat `IExtension` rozhraní. V tomto projektu vzorku `CustomLeaseExtension` třída obsahuje tato implementace.  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 `IExtension` Rozhraní má dvě metody `Attach` a `Detach`. Jako jejich názvy implikují, tyto dvě metody jsou volány při modul runtime připojí a odpojí rozšíření pro instance <xref:System.ServiceModel.InstanceContext> třídy. V této ukázce `Attach` metoda se používá ke sledování <xref:System.ServiceModel.InstanceContext> objekt, který patří na aktuální instanci rozšíření.  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 Kromě toho musíte přidat potřebné implementaci rozšíření poskytovat podporu delší doba platnosti. Proto `ICustomLease` rozhraní je deklarovaný s požadovanou metody a je implementována ve `CustomLeaseExtension` třídy.  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 Když vyvolá WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda v <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace toto volání se směruje na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodu `CustomLeaseExtension`. Pak se `CustomLeaseExtension` kontroluje stav privátní zobrazíte jestli <xref:System.ServiceModel.InstanceContext> nečinný. Pokud je nečinnosti se vrátí `true`. Jinak spustí časovač po zadanou dobu životnosti rozšířené.  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 V časovače `Elapsed` událost funkce zpětného volání v dispečera je volána, aby bylo možné spustit jinou vyčištění cyklus.  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 Neexistuje žádný způsob, jak obnovit časovač spuštěná, pokud dorazí novou zprávu pro instanci přesouvání do nečinného stavu.  
  
 Ukázka implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zachytávat volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda a směrování je `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Implementace je součástí `CustomLifetimeLease` třídy. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Metoda je volána, když je chcete uvolnit instance služby WCF. Je však pouze jednu instanci konkrétní `ISharedSessionInstance` implementace v ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekce. To znamená, že se nedá nijak zjistit, <xref:System.ServiceModel.InstanceContext> dochází k uzavření v době kontroluje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda. Proto tato ukázka používá zámek k serializaci požadavky na přístup z více vláken <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda.  
  
> [!IMPORTANT]
>  Použití vláken uzamčení není doporučený postup protože serializace vážně mohou ovlivnit výkon vaší aplikace.  
  
 Privátní členské proměnné se používá v `CustomLeaseExtension` třída sledovat `IsIdle` hodnotu. Pokaždé, když hodnota <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> se načte `IsIdle` privátního člena je vrácen a obnovit `false`. Je nezbytné k nastavení této hodnoty na `false` Pokud chcete mít jistotu dispečera volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda.  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 Pokud `ISharedSessionLifetime.IsIdle` vlastnost vrátí `false` dispečera zaregistruje funkci zpětného volání pomocí `NotifyIdle` metoda. Tato metoda přijímá odkaz na <xref:System.ServiceModel.InstanceContext> vydán. Proto můžete dotazovat ukázkový kód `ICustomLease` rozšíření typů a zkontrolujte `ICustomLease.IsIdle` vlastnost v rozšířených stavu.  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 Před `ICustomLease.IsIdle` vlastnost je zaškrtnuta možnost vlastnost zpětné volání je třeba nastavit, protože to je nezbytné pro `CustomLeaseExtension` dispečera upozornit, když se stane nečinnosti. Pokud `ICustomLease.IsIdle` vrátí `true`, `isIdle` privátního člena je jednoduše nastavena v `CustomLifetimeLease` k `true` a volá metodu zpětného volání. Protože kód obsahuje zámek, jiná vlákna nelze změnit hodnotu této privátního člena. A při příštím kontroluje dispečera `ISharedSessionLifetime.IsIdle`, vrátí `true` a umožňuje dispečera verzi instance.  
  
 Teď, když základ pro vlastní rozšíření bylo dokončeno, musí být připojených k modelu služby. Spojit `CustomLeaseExtension` implementace k <xref:System.ServiceModel.InstanceContext>, poskytuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> rozhraní k provedení zavádění z <xref:System.ServiceModel.InstanceContext>. V ukázce `CustomLeaseInitializer` třída implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` k <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekci z inicializace jedinou metodou. Tato metoda je volána dispečera při inicializaci <xref:System.ServiceModel.InstanceContext>.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 Nakonec `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` a <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementace je byl zapojen až modelu služby pomocí <xref:System.ServiceModel.Description.IServiceBehavior> implementace. Tato implementace je umístěn v `CustomLeaseTimeAttribute` třídy a také je odvozena z `Attribute` základní třída vystavit toto chování jako atribut. V `IServiceBehavior.ApplyBehavior` metoda, instancí <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> a `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementace jsou přidány do `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> kolekce <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> v uvedeném pořadí.  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 Toto chování lze přidat do třídu Ukázka služby podle její zadávání poznámek k `CustomLeaseTime` atribut.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>Viz také
