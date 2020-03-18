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
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400377"
---
# <a name="com-callable-wrapper"></a>Obálka volatelná aplikacemi COM

Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW). Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.

Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu. Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew. Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti. Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.

![Více klientů COM, kteří drží odkaz na CCW, který zveřejňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Com volatelné obálky jsou neviditelné pro ostatní třídy spuštěné v rámci běhu .NET. Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.

## <a name="object-identity"></a>Identita objektu

Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby. Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.

## <a name="object-lifetime"></a>Doba života objektu

Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM. Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt. Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.

## <a name="simulating-com-interfaces"></a>Simulace rozhraní COM

CCW zveřejňuje všechna veřejná rozhraní, rozhraní, datové typy a vrácené hodnoty klientům COM způsobem, který je v souladu s vynucením interakce založené na rozhraní com. Pro klienta COM je vyvolání metod na objektu .NET shodné s metodami vyvolání objektu COM.

Chcete-li vytvořit tento bezproblémový přístup, CCW vyrábí tradiční com rozhraní, jako je **například IUnknown** a **IDispatch**. Jak ukazuje následující obrázek, CCW udržuje jeden odkaz na objekt .NET, který obtéká. Klient COM i objekt .NET vzájemně spolupracují prostřednictvím proxy serveru a ověřování stavu dat konstrukce CCW.

![Diagram, který ukazuje, jak CCW vyrábí rozhraní COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Kromě vystavení rozhraní, které jsou explicitně implementovány třídou ve spravovaném prostředí, modul runtime .NET dodává implementace rozhraní COM uvedených v následující tabulce jménem objektu. Třída .NET může přepsat výchozí chování poskytnutím vlastní implementace těchto rozhraní. Modul runtime však vždy poskytuje implementaci pro rozhraní **IUnknown** a **IDispatch.**

|Rozhraní|Popis|
|---------------|-----------------|
|**Idispatch**|Poskytuje mechanismus pro pozdní vazbu na typ.|
|**Ierrorinfo**|Poskytuje textový popis chyby, její zdroj, soubor nápovědy, kontext nápovědy a identifikátor GUID rozhraní, které chybu definovalo (vždy **GUID_NULL** pro třídy .NET).|
|**IProvideClassInfo**|Umožňuje klientům COM získat přístup k rozhraní **ITypeInfo** implementovanému spravovanou třídou. Vrátí `COR_E_NOTSUPPORTED` na .NET Core pro typy, které nejsou importovány z com. |
|**ISupportErrorInfo**|Umožňuje klientovi COM určit, zda spravovaný objekt podporuje rozhraní **IErrorInfo.** Pokud ano, umožňuje klientovi získat ukazatel na nejnovější objekt výjimky. Všechny spravované typy podporují rozhraní **IErrorInfo.**|
|**ITypeInfo** (pouze rozhraní .NET Framework)|Poskytuje informace o typu pro třídu, která je přesně stejná jako informace o typu vytvořené tlbexp.exe.|
|**IUnknown**|Poskytuje standardní implementaci rozhraní **IUnknown,** se kterým klient COM spravuje životnost CCW a poskytuje typ nátlaku.|

 Spravovaná třída může také poskytnout rozhraní COM popsaná v následující tabulce.

|Rozhraní|Popis|
|---------------|-----------------|
|Rozhraní\_*třídy*( název třídy)|Rozhraní vystavené modulu runtime a není explicitně definováno, které zveřejňuje všechna veřejná rozhraní, metody, vlastnosti a pole, které jsou explicitně vystaveny spravovanému objektu.|
|**IConnectionPoint** a **IConnectionPointContainer**|Rozhraní pro objekty, které zdroj delegáta založené události (rozhraní pro registraci předplatitelů událostí).|
|**IDispatchEx** (pouze rozhraní .NET Framework)|Rozhraní dodané modulu runtime, pokud třída implementuje **IExpando**. Rozhraní **IDispatchEx** je rozšíření rozhraní **IDispatch,** které na rozdíl od **IDispatch**umožňuje výčet, sčítání, mazání a malá a velká písmena volání členů.|
|**IEnumVARIANT**|Rozhraní pro třídy typu kolekce, které vyjmenovává objekty v kolekci, pokud třída implementuje **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Představujeme rozhraní třídy

Rozhraní třídy, které není explicitně definováno ve spravovaném kódu, je rozhraní, které zveřejňuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně vystaveny na objektu .NET. Toto rozhraní může být duální nebo pouze pro odeslání rozhraní. Rozhraní třídy obdrží název samotné třídy .NET, před nímž je podtržítko. Například pro třídu Mammal je \_rozhraní třídy Mammal.

Pro odvozené třídy rozhraní třídy také zveřejňuje všechny veřejné metody, vlastnosti a pole základní třídy. Odvozené třídy také zpřístupňuje rozhraní třídy pro každou základní třídu. Například pokud třída Mammal rozšiřuje třídu MammalSuperclass, která sama rozšiřuje System.Object, objekt .NET \_zpřístupňuje klientům COM tři rozhraní třídy s názvem Mammal, \_MammalSuperclass a \_Object.

Zvažte například následující třídu .NET:

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

Klient COM může získat ukazatel na `_Mammal`rozhraní třídy s názvem . V rozhraní .NET Framework můžete použít nástroj [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) ke generování knihovny typů obsahující definici `_Mammal` rozhraní. Exportér knihovny typů není u jádra .NET podporován. Pokud `Mammal` třída implementována jedno nebo více rozhraní, rozhraní se zobrazí pod coclass.

```console
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

Generování rozhraní třídy je volitelné. Ve výchozím nastavení interop com generuje rozhraní pouze pro odeslání pro každou třídu, kterou exportujete do knihovny typů. Automatické vytváření tohoto rozhraní můžete zabránit nebo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> upravit použitím této třídy. Přestože rozhraní třídy může usnadnit úlohu vystavení spravovaných tříd com, jeho použití jsou omezené.

> [!CAUTION]
> Pomocí rozhraní třídy, namísto explicitně definování vlastní, může zkomplikovat budoucí správu verzí spravované třídy. Před použitím rozhraní třídy si přečtěte následující pokyny.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Definujte explicitní rozhraní pro klienty COM, které chcete použít, místo generování rozhraní třídy.

Vzhledem k tomu, že interop com generuje rozhraní třídy automaticky, změny po verzi vaší třídy můžete změnit rozložení rozhraní třídy vystavené modulu runtime společného jazyka. Vzhledem k tomu, že klienti COM jsou obvykle nepřipraveni na zpracování změn v rozložení rozhraní, přeruší se, pokud změníte rozložení členů třídy.

Tento pokyn posiluje představu, že rozhraní vystavená klientům COM musí zůstat neměnná. Chcete-li snížit riziko přerušení klientů COM neúmyslně změnit pořadí rozložení rozhraní, izolovat všechny změny třídy z rozložení rozhraní explicitně definování rozhraní.

Pomocí **classInterfaceAttribute** odpojit automatické generování rozhraní třídy a implementovat explicitní rozhraní pro třídu, jak ukazuje následující fragment kódu:

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

Hodnota **ClassInterfaceType.None** zabraňuje generování rozhraní třídy při exportu metadat třídy do knihovny typů. V předchozím příkladu mohou klienti `LoanApp` COM přistupovat `IExplicit` ke třídě pouze prostřednictvím rozhraní.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Vyhněte se ukládání identifikátorů odeslání do mezipaměti (DispIds)

Použití rozhraní třídy je přijatelnou možností pro skriptované klienty, klienty jazyka Microsoft Visual Basic 6.0 nebo všechny klienty s pozdní vazbou, který neukládá do mezipaměti dispIds členů rozhraní. DispIds identifikovat členy rozhraní povolit pozdní vazby.

Pro rozhraní třídy generování DispIds je založena na pozici člena v rozhraní. Pokud změníte pořadí člena a exportujete třídu do knihovny typů, změníte dispIds generované v rozhraní třídy.

Chcete-li se vyhnout porušení pozdní vázané klienty COM při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s **classInterfaceType.AutoDispatch** hodnotu. Tato hodnota implementuje rozhraní třídy pouze pro odeslání, ale vynese popis rozhraní z knihovny typů. Bez popisu rozhraní klienti nejsou schopni do mezipaměti DispIds v době kompilace. Přestože se jedná o výchozí typ rozhraní pro rozhraní třídy, můžete explicitně použít hodnotu atributu.

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

Chcete-li získat DispId člena rozhraní za běhu, mohou klienti COM volat **IDispatch.GetIdsOfNames**. Chcete-li vyvolat metodu v rozhraní, předejte vrácený DispId jako argument **IDispatch.Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Omezte pomocí možnosti duálního rozhraní pro rozhraní třídy.

Duální rozhraní umožňují včasné a pozdní vazby na členy rozhraní klienty COM. V době návrhu a během testování může být užitečné nastavit rozhraní třídy na duální. Pro spravovanou třídu (a její základní třídy), která se nikdy nezmění, je tato možnost také přijatelná. Ve všech ostatních případech se vyhněte nastavení rozhraní třídy na duální.

Automaticky generované duální rozhraní může být vhodné ve výjimečných případech; však častěji vytváří složitost související s verzí. Například klienti COM pomocí rozhraní třídy odvozené třídy můžete snadno přerušit se změnami základní třídy. Pokud třetí strana poskytuje základní třídu, rozložení rozhraní třídy je mimo vaši kontrolu. Dále, na rozdíl od rozhraní pouze pro odeslání, duální rozhraní **(ClassInterfaceType.AutoDual**) poskytuje popis rozhraní třídy v knihovně exportovaných typů. Takový popis povzbuzuje klienty s pozdní vazbou do mezipaměti DispIds v době kompilace.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Ujistěte se, že všechna oznámení událostí COM jsou pozdní vazba.

Ve výchozím nastavení jsou informace o typu COM vloženy přímo do spravovaných sestavení, což eliminuje potřebu primárních meziop sestavení (PIA). Jedním z omezení informací o vloženém typu je však, že nepodporuje doručování oznámení událostí COM pomocí volání `IDispatch::Invoke` vtable s časnou vazbou, ale podporuje pouze volání s pozdní vazbou.

Pokud vaše aplikace vyžaduje volání včasného vázaného na metody rozhraní událostí COM, můžete `true`nastavit vlastnost **Embed Interop Types** v sadě Visual Studio nebo zahrnout do souboru projektu následující prvek:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Obálky COM](com-wrappers.md)
- [Vystavení komponent architektury .NET Framework pro COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Vystavení komponent .NET Core pro COM](../../core/native-interop/expose-components-to-com.md)
- [Kvalifikace typů .NET pro spolupráci](qualify-net-types-for-interoperation.md)
- [Obálka volatelná za běhu](runtime-callable-wrapper.md)
