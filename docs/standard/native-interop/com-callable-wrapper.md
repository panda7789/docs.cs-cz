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
ms.openlocfilehash: ebfc8f79303f89b092dd0fb38237dffffe0a93ba
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353916"
---
# <a name="com-callable-wrapper"></a>Obálka volatelná aplikacemi COM

Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW). Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.

Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu. Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew. Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti. Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.

![Několik klientů modelu COM drží odkaz na doleva, který zpřístupňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Obálky s příchodem modelu COM jsou neviditelné pro jiné třídy běžící v prostředí .NET Runtime. Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.

## <a name="object-identity"></a>Identita objektu

Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby. Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.

## <a name="object-lifetime"></a>Doba života objektu

Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM. Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt. Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.

## <a name="simulating-com-interfaces"></a>Simulace rozhraní COM

DOLEVA zpřístupňuje všechna veřejná, rozhraní viditelná v modelu COM, datové typy a návratové hodnoty klientům modelu COM způsobem, který je konzistentní s vynucováním interakce založených na rozhraních modelu COM. V případě klienta modelu COM je vyvolání metod objektu rozhraní .NET identické s voláním metod objektu COM.

Pro vytvoření tohoto bezproblémového přístupu se v doleva vyrábí tradiční rozhraní COM, jako je **IUnknown** a **IDispatch**. Jak ukazuje následující obrázek, doleva udržuje jediný odkaz na objekt .NET, který se zalomí. Klient COM i objekt rozhraní .NET vzájemně komunikují prostřednictvím proxy serveru a vytváření zástupných procedur v rámci služby doleva.

![Diagram znázorňující, jak doleva vyrábí rozhraní COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Kromě vystavení rozhraní, která jsou explicitně implementována třídou ve spravovaném prostředí, modul runtime .NET poskytuje implementaci rozhraní COM uvedená v následující tabulce jménem objektu. Třída .NET může přepsat výchozí chování tím, že poskytuje vlastní implementaci těchto rozhraní. Modul runtime však vždy poskytuje implementaci rozhraní **IUnknown** a **IDispatch** .

|Rozhraní|Popis|
|---------------|-----------------|
|**IDispatch**|Poskytuje mechanismus pro pozdní vazbu na typ.|
|**IErrorInfo**|Poskytuje textový popis chyby, její zdroj, soubor s nápovědu, kontext nápovědu a identifikátor GUID rozhraní, které definuje chybu (vždy **GUID_NULL** pro třídy .NET).|
|**IProvideClassInfo**|Umožňuje klientům modelu COM získat přístup k rozhraní **volání ITypeInfo** implementovanému spravovanou třídou. Vrátí `COR_E_NOTSUPPORTED` v .NET Core pro typy, které nejsou naimportované z modelu COM. |
|**ISupportErrorInfo**|Umožňuje klientovi modelu COM určit, zda spravovaný objekt podporuje rozhraní **IErrorInfo** . Pokud ano, umožňuje klientovi získat ukazatel na nejnovější objekt výjimky. Všechny spravované typy podporují rozhraní **IErrorInfo** .|
|**Volání ITypeInfo** (pouze .NET Framework)|Poskytuje informace o typu pro třídu, která je přesně stejná jako informace o typu vytvořené nástrojem Tlbexp. exe.|
|**IUnknown**|Poskytuje standardní implementaci rozhraní **IUnknown** , se kterým klient modelu COM spravuje dobu života doleva a poskytuje převod typu.|

 Spravovaná třída může také poskytovat rozhraní COM popsaná v následující tabulce.

|Rozhraní|Popis|
|---------------|-----------------|
|Rozhraní třídy (\_*ClassName*)|Rozhraní vystavené modulem runtime a není explicitně definováno, které zveřejňuje všechna veřejná rozhraní, metody, vlastnosti a pole, které jsou explicitně vystaveny na spravovaném objektu.|
|**IConnectionPoint** a **IConnectionPointContainer**|Rozhraní pro objekty, které jsou zdrojem událostí založených na delegátech (rozhraní pro registraci předplatitelů událostí).|
|**IDispatchEx –** (pouze .NET Framework)|Rozhraní dodávané modulem runtime, pokud třída implementuje **IExpando**. Rozhraní **IDispatchEx –** je rozšíření rozhraní **IDispatch** , které na rozdíl od rozhraní **IDispatch**povoluje vyčíslení, sčítání, odstraňování a rozlišování velkých a malých písmen členů.|
|**IEnumVARIANT**|Rozhraní tříd typu kolekce, které vyčíslují objekty v kolekci, pokud třída implementuje rozhraní **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Představení rozhraní třídy

Rozhraní třídy, které není explicitně definováno ve spravovaném kódu, je rozhraní, které zpřístupňuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně vystaveny na objektu rozhraní .NET. Toto rozhraní může být rozhraní pouze pro duální nebo pouze pro odesílání. Rozhraní třídy přijímá název samotné třídy .NET, před kterým předchází podtržítko. Například pro savce tříd je rozhraní třídy \_Mammal.

U odvozených tříd rozhraní třídy také zveřejňuje všechny veřejné metody, vlastnosti a pole základní třídy. Odvozená třída také zpřístupňuje rozhraní třídy pro každou základní třídu. Například pokud třídy savců rozšiřuje třídu MammalSuperclass, která sám rozšiřuje System. Object, objekt .NET zpřístupňuje klientům modelu COM tři rozhraní třídy s názvem \_Mammal, \_MammalSuperclass a \_Object.

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

Klient COM může získat ukazatel na rozhraní třídy s názvem `_Mammal`. V .NET Framework můžete použít nástroj [Exportér knihovny typů (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) pro vygenerování knihovny typů obsahující definici rozhraní `_Mammal`. Exportér knihovny typů není v rozhraní .NET Core podporován. Pokud třída `Mammal` implementovala jedno nebo více rozhraní, zobrazí se rozhraní v rámci třídy coclass.

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

Generování rozhraní třídy je volitelné. Ve výchozím nastavení zprostředkovatel komunikace s objekty COM generuje pro každou třídu, kterou exportujete do knihovny typů, rozhraní pouze pro odesílání. Automatickému vytváření tohoto rozhraní můžete zabránit nebo upravit tak, že použijete <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do vaší třídy. I když rozhraní třídy může zjednodušit úlohu vystavení spravovaných tříd modelu COM, jejich použití je omezeno.

> [!CAUTION]
> Použití rozhraní třídy namísto explicitního definování vlastního může zkomplikovat budoucí verze spravované třídy. Než použijete rozhraní třídy, přečtěte si následující pokyny.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Definujte explicitní rozhraní pro klienty modelu COM, aby bylo možné použít místo generování rozhraní třídy.

Vzhledem k tomu, že zprostředkovatel komunikace s objekty COM generuje rozhraní třídy automaticky, změny po změně verze vaší třídy mohou změnit rozložení rozhraní třídy vystavené modulem CLR (Common Language Runtime). Vzhledem k tomu, že klienti modelu COM jsou obvykle nepřipraveni zpracovávat změny v rozložení rozhraní, jsou přerušeny při změně rozložení členů třídy.

Tento návod posiluje pojem, že rozhraní vystavená klientům modelu COM musejí zůstat nezměněná. Chcete-li snížit riziko narušení klientů modelu COM neúmyslným přeřazením rozložení rozhraní, izolujte všechny změny třídy z rozložení rozhraní explicitním definováním rozhraní.

Použijte **ClassInterfaceAttribute** k diskrokování automatické generace rozhraní třídy a implementaci explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:

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

Hodnota **ClassInterfaceType. None** zabraňuje tomu, aby se rozhraní třídy vygenerovalo, když se metadata třídy exportují do knihovny typů. V předchozím příkladu můžou klienti modelu COM přistupovat ke třídě `LoanApp` pouze prostřednictvím rozhraní `IExplicit`.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Vyhněte se neukládání do mezipaměti pro odesílání (identifikátory spId)

Použití rozhraní třídy je přijatelná možnost pro skripty spouštěné klienty, klienty Microsoft Visual Basic 6,0 nebo jakéhokoli klienta s pozdní vazbou, který neukládá do mezipaměti identifikátory spId členů rozhraní. Odidentifikátory DISPID identifikují členy rozhraní, aby umožnily pozdní vazbu.

Pro rozhraní třídy je generování identifikátorů DISPID založeno na pozici člena v rozhraní. Změníte-li pořadí člena a vyexportujete třídu do knihovny typů, změníte identifikátory spId vygenerované v rozhraní třídy.

Aby nedocházelo k přerušení klientů modelu COM s pozdní vazbou při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s hodnotou **ClassInterfaceType. Dispatch** . Tato hodnota implementuje rozhraní třídy pouze pro odesílání, ale z knihovny typů je vynechán Popis rozhraní. Bez popisu rozhraní nemůžou klienti v době kompilace ukládat do mezipaměti identifikátory spId. Přestože se jedná o výchozí typ rozhraní pro rozhraní třídy, můžete hodnotu atributu použít explicitně.

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

Chcete-li získat DispId člena rozhraní v době běhu, mohou klienti modelu COM volat metodu **IDispatch. GetIDsOfNames**. Chcete-li vyvolat metodu v rozhraní, předejte vrácenou hodnotu DispId jako argument do metody **IDispatch. Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Omezte použití možnosti duálního rozhraní pro rozhraní třídy.

Duální rozhraní umožňují předčasné a pozdní vazbu na členy rozhraní podle klientů modelu COM. V době návrhu a během testování může být užitečné nastavit rozhraní třídy na hodnotu duální. Pro spravovanou třídu (a její základní třídy), která se nikdy neupraví, je tato možnost také přijatelná. Ve všech ostatních případech Vyhněte nastavení rozhraní třídy na hodnotu duální.

Ve výjimečných případech může být vhodné automaticky vygenerované duální rozhraní. častěji ale vytváří složitost související s verzí. Například klienti modelu COM používající rozhraní třídy odvozené třídy mohou snadno přerušit změny základní třídy. Pokud třetí strana poskytne základní třídu, rozložení rozhraní třídy je mimo ovládací prvek. Na rozdíl od rozhraní pouze pro odesílání, duální rozhraní (**ClassInterfaceType. AutoDual**) poskytuje popis rozhraní třídy v exportované knihovně typů. Tento popis podporuje klienty s pozdní vazbou na ukládání identifikátorů spId do mezipaměti v době kompilace.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Ujistěte se, že všechna oznámení o událostech COM jsou pozdní vazba.

Ve výchozím nastavení jsou informace o typu modelu COM vloženy přímo do spravovaných sestavení, což eliminuje nutnost primárních definičních sestavení (PIA). Jedno z omezení vloženého typu informací však znamená, že nepodporuje doručování oznámení o událostech modelu COM pomocí volání vtable s časnou vazbou, ale podporuje pouze volání s pozdní vazbou `IDispatch::Invoke`.

Pokud vaše aplikace vyžaduje volání s časnou vazbou na metody rozhraní COM události, můžete nastavit vlastnost **Embed Interop Types** v sadě Visual Studio na `true` nebo do souboru projektu zahrnout následující prvek:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [COM – obálky](com-wrappers.md)
- [Vystavení komponent architektury .NET Framework pro COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Vystavení součástí .NET Core pro COM](../../core/native-interop/expose-components-to-com.md)
- [Kvalifikace typů .NET pro spolupráci](qualify-net-types-for-interoperation.md)
- [Obálka volatelná za běhu](runtime-callable-wrapper.md)
