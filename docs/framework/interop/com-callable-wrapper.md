---
title: "Obálka volatelná aplikacemi COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 874550511ed04427003f6fd54fdd97b3001356fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="com-callable-wrapper"></a>Obálka volatelná aplikacemi COM
Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW). Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.  
  
 Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu. Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew. Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti. Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.  
  
 ![Obálka volatelná aplikacemi COM](../../../docs/framework/interop/media/ccw.gif "doleva")  
Přístup k objektům rozhraní .NET prostřednictvím obálky volatelné modelem COM  
  
 Obálky volatelné modelem COM jsou pro ostatní třídy, které jsou spuštěny v rámci rozhraní .NET Framework, neviditelné. Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.  
  
## <a name="object-identity"></a>Identity – objekt  
 Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby. Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.  
  
## <a name="object-lifetime"></a>Doba života objektu  
 Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM. Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt. Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.  
  
## <a name="simulating-com-interfaces"></a>Simulaci COM – rozhraní  
 [Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) (doleva) zpřístupní všechny veřejné, rozhraní COM – viditelné, datové typy a návratové hodnoty klientům COM způsobem, který je v souladu s COM na vynucení založené na rozhraní interakce. Pro klienta COM volání metod v rozhraní .NET Framework objektu je stejný jako k vyvolání metody u objektu COM.  
  
 Pokud chcete vytvořit tento bezproblémový přístup, doleva vyrábí tradiční rozhraní modelu COM, například **IUnknown** a **IDispatch**. Jak ukazuje následující obrázek, doleva udržuje jeden odkaz na objekt .NET, který se zabalí. Klient COM i rozhraní .NET objekt vzájemně spolupracovat prostřednictvím proxy serveru a se zakázaným inzerováním konstrukce CCW.  
  
 ![COM – rozhraní](../../../docs/framework/interop/media/ccwwithinterfaces.gif "ccwwithinterfaces")  
Rozhraní COM a obálka volatelná aplikacemi COM  
  
 Kromě vystavení rozhraní, které jsou explicitně implementované třídou ve spravovaném prostředí, rozhraní .NET Framework poskytuje implementace rozhraní modelu COM, které jsou uvedené v následující tabulce jménem objekt. Třída rozhraní .NET můžete přepsat výchozí chování tím, že poskytuje vlastní implementaci těchto rozhraní. Ale modulu runtime vždy poskytuje implementaci pro **IUnknown** a **IDispatch** rozhraní.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IDispatch**|Poskytuje mechanismus pro pozdní vazbu na typ.|  
|**IerrorInfo**|Obsahuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro rozhraní .NET třídy).|  
|**IprovideClassInfo**|Umožňuje klientům získat přístup k modelu COM **ITypeInfo** rozhraní implementované spravovanou třídou.|  
|**IsupportErrorInfo**|Umožňuje klientovi COM, abyste zjistili, jestli podporuje spravovaného objektu **IErrorInfo** rozhraní. Pokud ano, umožňuje klientům získat ukazatele na nejnovější objekt výjimky. Všechny typy podpora spravovaného **IErrorInfo** rozhraní.|  
|**ItypeInfo**|Poskytuje informace o typu pro třídu, která je stejná jako informace o typu vytvářených Tlbexp.exe.|  
|**IUnknown**|Poskytuje standardní implementace **IUnknown** rozhraní, se kterým klient COM spravuje životnost doleva a poskytuje převod typu.|  
  
 Spravované třídy můžete zadat taky rozhraní modelu COM, které jsou popsané v následující tabulce.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|(_*Classname*) rozhraní – třída|Rozhraní, vystavené modulu runtime a nejsou explicitně definovány, který zpřístupní všechny veřejné rozhraní, metody, vlastnosti a pole, která jsou explicitně zveřejněné na spravovaného objektu.|  
|**IConnectionPoint –** a **IconnectionPointContainer**|Rozhraní pro objekty, které zdroje události na základě delegáta (rozhraní pro registraci události odběratele).|  
|**IdispatchEx**|Zadaný modulem runtime, pokud třída implementuje rozhraní **IExpando**. **IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a to malá a velká písmena volání metody členů.|  
|**IEnumVARIANT**|Rozhraní pro typ kolekce tříd, které vytvoří výčet objektů v kolekci, pokud třída implementuje **rozhraní IEnumerable**.|  
  
## <a name="introducing-the-class-interface"></a>Představení rozhraní – třída  
 Třída rozhraní, které nejsou výslovně definované ve spravovaném kódu, je rozhraní, které vystavuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně zveřejněné na objekt .NET. Toto rozhraní může být dva nebo pouze pro odeslání rozhraní. Třída rozhraní obdrží název třídy rozhraní .NET, samostatně, podtržítko před sebou. Třída rozhraní je pro třídu savec _Mammal.  
  
 Odvozené třídy rozhraní třída taky zpřístupňuje všechny veřejné metody, vlastnosti a pole základní třídy. Odvozené třídy taky zpřístupňuje rozhraní třídy pro každou základní třídu. Například pokud třída savec rozšiřuje třídu MammalSuperclass, které rozšiřuje System.Object, vystavuje rozhraní modelu COM klienti tři třídy s názvem _Mammal, _MammalSuperclass a _Object objekt .NET.  
  
 Zvažte například následující třídy rozhraní .NET:  
  
```vb  
' Applies the ClassInterfaceAttribute to set the interface to dual.  
<ClassInterface(ClassInterfaceType.AutoDual)> _  
' Implicitly extends System.Object.  
Public Class Mammal  
    Sub Eat()  
    Sub Breathe()  
    Sub Sleep()  
End Class  
```  
  
```csharp  
// Applies the ClassInterfaceAttribute to set the interface to dual.  
[ClassInterface(ClassInterfaceType.AutoDual)]  
// Implicitly extends System.Object.  
public class Mammal  
{  
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 Klient COM můžete získat ukazatele na třídu rozhraní s názvem `_Mammal`, který je popsaný v knihovně typu, [Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) nástroj, který generuje. Pokud `Mammal` třída implementovat jednu nebo více rozhraní, rozhraní se zobrazí v části coclass.  
  
```  
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]  
interface _Mammal : IDispatch  
{  
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*  
        pRetVal);  
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]  
        VARIANT_BOOL* pRetVal);  
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);  
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);  
    [id(0x6002000d)] HRESULT Eat();  
    [id(0x6002000e)] HRESULT Breathe();  
    [id(0x6002000f)] HRESULT Sleep();  
}  
[uuid(…)]  
coclass Mammal   
{  
    [default] interface _Mammal;  
}  
```  
  
 Generování rozhraní třída je volitelný. Ve výchozím nastavení generuje zprostředkovatel komunikace s objekty COM rozhraní, které je určené pouze pro jednotlivé třídy, které můžete exportovat do knihovny typů. Můžete zakázat nebo upravit automatické vytvoření tohoto rozhraní s použitím <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> na třídu. I když je třída rozhraní můžete zjednodušují vystavení spravované třídy do modelu COM, jeho použití jsou omezené.  
  
> [!CAUTION]
>  Pomocí třídy rozhraní, namísto výslovně definování vlastní, může zkomplikovat budoucí verze vaší spravované třídy. Před použitím rozhraní třída přečtěte si následující pokyny.  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Zadejte explicitní rozhraní COM klientům použít nikoli generování rozhraní třídy.  
 Vzhledem k tomu, že zprostředkovatel komunikace s objekty COM automaticky vygeneruje třídu rozhraní, můžete změny po verze vaší třídy změnit rozložení rozhraní třída vystavené modul common language runtime. Vzhledem k tomu, že jsou klienti COM obvykle neupravený zpracovat změny v rozložení rozhraní, přerušení při změně rozložení člena třídy.  
  
 Toto platí posiluje zápisu, rozhraní, které jsou vystavené klientům COM musí zůstat neměnný. Aby se snížilo riziko nejnovější klientů modelu COM pomocí nechtěně Změna rozložení rozhraní, izolovat všechny změny do třídy z rozhraní rozložení explicitně definováním rozhraní.  
  
 Použití **ClassInterfaceAttribute** musí vypnout automatické generování třídy rozhraní a implementace explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 **ClassInterfaceType.None** hodnota zabraňuje rozhraní třída generován při metadata tříd se exportují do knihovny typů. V předchozím příkladu, mohou mít přístup klienti COM `LoanApp` pouze prostřednictvím třídy `IExplicit` rozhraní.  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Vyhněte se ukládání do mezipaměti identifikátorů odesílání (hodnoty DISPID).  
 Pomocí třídy rozhraní je přijatelné možnost pro skriptované klientů, Microsoft Visual Basic 6.0 nebo libovolného klienta pozdní vazbou, který neukládá do mezipaměti hodnoty dispID rozhraní členů. Hodnoty dispID identifikovat členové rozhraní povolit pozdní vazba.  
  
 Pro rozhraní třídy generování hodnoty dispID vychází z pozice člena v rozhraní. Je-li změnit pořadí člena a exportovat třídu do knihovny typů, změní se hodnoty dispID generované třídy rozhraní.  
  
 Pokud chcete vyhnout pozastavení klienti COM pozdní vazbou při pomocí třídy rozhraní, použít **ClassInterfaceAttribute** s **ClassInterfaceType.AutoDispatch** hodnotu. Tato hodnota implementuje rozhraní, které je určené pouze pro třídy, ale vynechá popis rozhraní z knihovny typů. Bez popisu rozhraní se klienti nemohou doba kompilace hodnoty dispID v mezipaměti. Přestože je toto výchozí typ rozhraní pro třídu rozhraní, můžete použít hodnotu atributu explicitně.  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 Chcete-li získat DispId člena rozhraní za běhu, klienti COM zavolat **IDispatch.GetIdsOfNames**. Pro vyvolání metody na rozhraní, předat jako argument pro vrácené DispId **IDispatch.Invoke**.  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Omezte pomocí možnosti duální rozhraní pro třídu rozhraní.  
 Duální rozhraní povolit časná a pozdní vazbu na členy rozhraní COM klienty. V době návrhu a během testování může být užitečné nastavit rozhraní třídy na dva. Pro spravované třídy (a její základní třídy), nikdy nebudou změněna, tato možnost je také přijatelné. Ve všech ostatních případech Vyhněte se nastavení rozhraní třída Dual.  
  
 Duální rozhraní automaticky generované může být vhodné ve výjimečných případech; ale častěji vytvoří verze související složitost. Například klientů modelu COM pomocí rozhraní třídy odvozené třídy můžete snadno rozdělit změn v základní třídě. Když třetích stran poskytuje základní třídu, rozložení rozhraní třída je mimo vlastního ovládacího prvku. Na rozdíl od určené pouze pro rozhraní, další dva rozhraní (**ClassInterface.AutoDual**) obsahuje popis rozhraní – třída v knihovně exportovaný typu. Tento popis doporučuje pozdní vazbou klientům mezipaměti hodnoty dispID za běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md)  
 [COM – obálky](../../../docs/framework/interop/com-wrappers.md)  
 [Vystavení součástí .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Simulace COM – rozhraní](http://msdn.microsoft.com/en-us/ad2ab959-e2be-411b-aaff-275c3fba606c)  
 [Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [Obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md)
