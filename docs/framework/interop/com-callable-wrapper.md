---
title: Obálka volatelná aplikacemi COM
ms.date: 10/23/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6d205cc9b13a43cd3b519c2a262f3db767ace7b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309482"
---
# <a name="com-callable-wrapper"></a>Obálka volatelná aplikacemi COM

Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW). Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.

Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu. Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew. Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti. Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.

![Více klientům modelu COM, která uchovává odkaz na objekt CCW, který zpřístupňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Obálky volatelné modelem COM jsou pro ostatní třídy, které jsou spuštěny v rámci rozhraní .NET Framework, neviditelné. Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.

## <a name="object-identity"></a>Identita objektu

Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby. Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.

## <a name="object-lifetime"></a>Doba života objektu

Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM. Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt. Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.

## <a name="simulating-com-interfaces"></a>Simulace rozhraní COM

Objekt CCW zpřístupňuje všechny veřejné, viditelný modulem COM rozhraní, datových typů a návratové hodnoty klientům modelu COM způsobem, který je konzistentní s modelu COM vynucení interakce založené na rozhraní. Klient modelu COM volání metod pro objekt rozhraní .NET Framework je stejný jako volání metod na objekt modelu COM.

Chcete-li vytvořit tento bezproblémový přístup, objekt CCW vyrábí tradiční rozhraní modelu COM, jako například **IUnknown** a **IDispatch**. Jak ukazuje následující obrázek, objekt CCW udržuje jeden odkaz na objekt .NET, který ho zalamoval. Klient COM a objektu rozhraní .NET komunikovat mezi sebou prostřednictvím proxy a zástupných procedur konstrukce CCW.

![Diagram znázorňující, jak objekt CCW vyrábí rozhraní modelu COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Kromě zpřístupnění rozhraní, která jsou explicitně implementováno třídou ve spravovaném prostředí, rozhraní .NET Framework poskytuje implementace rozhraní modelu COM, které jsou uvedeny v následující tabulce jménem objekt. Třída rozhraní .NET výchozí chování můžete přepsat tím, že poskytuje vlastní implementaci těchto rozhraní. Nicméně vždy modul runtime poskytuje implementaci pro **IUnknown** a **IDispatch** rozhraní.

|Rozhraní|Popis|
|---------------|-----------------|
|**IDispatch**|Poskytuje mechanismus pro pozdní vazbu na typ.|
|**IErrorInfo**|Poskytuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro třídy .NET).|
|**IProvideClassInfo**|Umožňuje získat přístup ke klientům modelu COM **ITypeInfo** rozhraní implementovány pomocí spravované třídy.|
|**ISupportErrorInfo**|Umožňuje určit, zda spravovaný objekt podporuje klient modelu COM **IErrorInfo** rozhraní. Pokud ano, umožňuje klientům získat ukazatel objektu nejnovější výjimky. Všechny spravované typy podporu **IErrorInfo** rozhraní.|
|**ITypeInfo**|Poskytuje informace o typu pro třídu, která je stejná jako informace o typu, který je vytvořený pomocí Tlbexp.exe.|
|**IUnknown**|Poskytuje standardní implementace **IUnknown** rozhraní, se kterým klient modelu COM, spravuje životnost objekt CCW a obsahuje převod typu.|

 Spravované třídy můžete také zadat rozhraní modelu COM, které jsou popsány v následující tabulce.

|Rozhraní|Popis|
|---------------|-----------------|
|(\_*Classname*) rozhraní třídy|Rozhraní vystavena modulem runtime a nejsou explicitně definovány, která poskytuje veřejná rozhraní, metody, vlastnosti a pole, která dostanou na spravovaný objekt.|
|**IConnectionPoint** a **IConnectionPointContainer**|Rozhraní pro objekty, které zdroj události na základě delegáta (rozhraní pro registraci odběratelů událostí).|
|**Rozhraní IDispatchEx**|Zadaný modul runtime, pokud třída implementuje rozhraní **IExpando**. **Rozhraní IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a malá a velká písmena volání členů.|
|**IEnumVARIANT**|Rozhraní pro typ kolekce tříd, které vytvoří výčet objektů v kolekci, pokud třída implementuje **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Představení rozhraní třídy

Rozhraní třídy, které nejsou výslovně definované ve spravovaném kódu, je rozhraní, který zpřístupňuje všechny veřejné metody, vlastnosti, pole a události, které se dostanou na objekt .NET. Toto rozhraní může být duální nebo určené pouze pro rozhraní. Rozhraní třídy přijímá název třídy .NET, začínající podtržítkem. Například pro třídu savec, je třída rozhraní \_savec.

Odvozené třídy rozhraní třídy také zpřístupní všechny veřejné metody, vlastnosti a pole základní třídy. Odvozená třída také poskytuje rozhraní třídy pro každou ze základních tříd. Například pokud třída savec rozšiřuje třídu MammalSuperclass, které rozšiřuje System.Object, .NET zpřístupňuje objektů klienty modelu COM tři třídy rozhraní s názvem \_savec, \_MammalSuperclass, a \_objektu.

Představte si třeba následující třídy .NET:

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
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

Klient modelu COM může získání ukazatele na třídy rozhraní s názvem `_Mammal`, který je popsaný v knihovně typů, které [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) Nástroj generuje. Pokud `Mammal` jedno nebo více rozhraní implementované třídy, rozhraní by se zobrazí pod coclass.

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

Generování třídy rozhraní je volitelné. Ve výchozím nastavení spolupráci s COM generuje určené pouze pro rozhraní pro každou třídu, která exportujete do knihovny typů. Můžete zakázat nebo upravit automatické vytváření tohoto rozhraní použitím <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do vaší třídy. Přestože rozhraní třídy můžete usnadnění vystavení spravované třídy modelu COM, jeho použití jsou omezené.

> [!CAUTION]
> Pomocí třídy rozhraní, namísto explicitně definovat vlastní, může zkomplikovat budoucích verzí spravované třídy. Před použitím rozhraní si přečtěte následující pokyny.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Definujte explicitní rozhraní klientům modelu COM použít nikoli generování třídy rozhraní.

Protože komunikace s objekty COM automaticky vygeneruje třídy rozhraní, můžete změnit po verzi změny do vaší třídy rozložení třídy rozhraní vystavené modul common language runtime. Protože klienti modelu COM jsou obvykle připraven zpracovat změny v rozložení rozhraní, přerušit při změně rozložení třídy.

Toto pravidlo zvyšuje pojem, musí zůstat jakákoliv zveřejněné klientům modelu COM rozhraní. Aby se snížilo riziko rozbíjející klientům modelu COM opětovným uspořádáním neúmyslně rozložení rozhraní, izolují všechny změny do třídy z rozložení rozhraní explicitně definováním rozhraní.

Použití **ClassInterfaceAttribute** musí vypnout automatické generování rozhraní, třídy a implementace explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

**ClassInterfaceType.None** hodnota zabraňuje rozhraní generovaných při exportu metadat třídy do knihovny typů. V předchozím příkladu, můžete přístup ke klientům modelu COM `LoanApp` pouze prostřednictvím třídy `IExplicit` rozhraní.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Vyhněte se ukládání do mezipaměti identifikátory odesílání (DISPID)

Pomocí rozhraní třídy je přijatelný varianta pro skriptované klientů, Microsoft Visual Basic 6.0 nebo jakéhokoli klienta s pozdní vazbou, která neukládá do mezipaměti dispID členy rozhraní. Hodnoty dispID určit členy rozhraní umožňující pozdní vazbu.

Pro rozhraní třídy generování hodnoty dispID podle pozice člena v rozhraní. Je-li změnit pořadí členů a exportovat třídy do knihovny typů, změní hodnoty dispID generované třídy rozhraní.

Chcete-li vyhnuli narušení funkčnosti klientů modelu COM s pozdní vazbou, při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s **ClassInterfaceType.AutoDispatch** hodnotu. Tato hodnota implementuje rozhraní určené pouze pro třídy, ale vynechá popis rozhraní z knihovny typů. Bez případně popis rozhraní klienti nebudou moct mezipaměti hodnoty dispID v době kompilace. I když se jedná o výchozí typ rozhraní pro rozhraní, můžete explicitně použít hodnotu atributu.

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

Chcete-li získat identifikátor DispId člena rozhraní v době běhu, můžete volat klientům modelu COM **IDispatch.GetIdsOfNames**. K vyvolání metody v rozhraní, předat jako argument pro DispId vrácená **IDispatch.Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Omezte použití možnosti duální rozhraní pro rozhraní třídy.

Duální rozhraní povolit časná a pozdní vazby pro členy rozhraní modelu COM klienty. V době návrhu a během testování může být užitečné nastavit na duální rozhraní třídy. Pro spravovanou třídu (a její základní třídy), která nebude nikdy změněn, tato možnost je také přijatelné. Ve všech ostatních případech nenastavujte na duální rozhraní třídy.

Automaticky generované duální rozhraní může být vhodné ve výjimečných případech; ale častěji vytvoří související verze složitost. Například klienti modelu COM pomocí rozhraní třídy odvozené třídy může snadno překročit se změnami na základní třídu. Při jiného výrobce poskytuje základní třídu, je rozložení rozhraní třídy mimo ovládací prvek. Na rozdíl od rozhraní určené pouze pro odesílání, další duální rozhraní (**ClassInterfaceType.AutoDual**) obsahuje popis rozhraní třídy v exportované knihovny typů. Tento popis podporuje klienty s pozdní vazbou do mezipaměti hodnoty dispID v době běhu.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Ujistěte se, že jsou všechna oznámení událostí modelu COM s pozdní vazbou.

Ve výchozím nastavení informace o typu modelu COM se vloží přímo do spravovaných sestavení, která eliminuje potřebu primárního sestavení interop (PIA). Jeden z omezení vložené informace o typu je však, že volání časné vazby vtable nepodporuje doručování oznámení událostí modelu COM, ale podporuje pouze s pozdní vazbou `IDispatch::Invoke` volání.

Pokud vaše aplikace vyžaduje volání časné vazby na metody rozhraní události modelu COM, můžete nastavit **Embed Interop Types** v sadě Visual Studio k `true`, nebo obsahovat následující element v souboru projektu:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Obálky COM](com-wrappers.md)
- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Kvalifikace typů .NET pro spolupráci](qualifying-net-types-for-interoperation.md)
- [Obálka volatelná za běhu](runtime-callable-wrapper.md)
