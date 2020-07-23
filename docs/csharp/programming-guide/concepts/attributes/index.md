---
title: Atributy (C#)
description: Naučte se, jak pomocí atributů přidružit metadata nebo deklarativní informace k kódu v jazyce C#. Atribut může být dotazován v době běhu pomocí reflexe.
ms.date: 04/26/2018
ms.openlocfilehash: 5c57838b649531d8e8fe89919771adf8830e7f54
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924982"
---
# <a name="attributes-c"></a>Atributy (C#)

Atributy poskytují výkonnou metodu přidružování metadat nebo deklarativní informace, s kódem (sestavení, typy, metodami, vlastnostmi a tak dále). Po přiřazení atributu k entitě programu lze pomocí metody s názvem *reflexe*zadat dotaz na atribut v době běhu. Další informace naleznete v tématu [reflexe (C#)](../reflection.md).

Atributy mají následující vlastnosti:

- Atributy přidávají do programu metadata. *Metadata* jsou informace o typech definovaných v programu. Všechna sestavení .NET obsahují zadanou sadu metadat, které popisují typy a členy typu definované v sestavení. Můžete přidat vlastní atributy a zadat případné další požadované informace. Další informace naleznete v tématu a [vytváření vlastních atributů (C#)](creating-custom-attributes.md).
- Jeden nebo více atributů lze použít pro celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.
- Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.
- Váš program může prošetřit vlastní metadata nebo metadata v jiných programech pomocí reflexe. Další informace naleznete v tématu [přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Použití atributů

Atributy lze umístit na většinu jakékoli deklarace, i když konkrétní atribut může omezit typy deklarací, na kterých je platný. V jazyce C# zadáte atribut tak, že umístíte název atributu uzavřený do hranatých závorek ([]) nad deklaraci entity, na kterou se vztahuje.

V tomto příkladu <xref:System.SerializableAttribute> je atribut použit k použití konkrétní charakteristiky pro třídu:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována jako v následujícím příkladu:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

V deklaraci lze umístit více než jeden atribut, jak ukazuje následující příklad:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Některé atributy lze pro danou entitu zadat více než jednou. Příklad takového atributu Multiuse je <xref:System.Diagnostics.ConditionalAttribute> :

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Podle konvence názvy všech atributů končí slovem "Attribute", aby je bylo možné odlišit od ostatních položek v knihovnách .NET. Při použití atributů v kódu však není nutné zadávat příponu atributu. Například `[DllImport]` je ekvivalentní k `[DllImportAttribute]` , ale `DllImportAttribute` je skutečným názvem atributu v knihovně tříd .NET.

### <a name="attribute-parameters"></a>Parametry atributu

Mnoho atributů má parametry, které mohou být pozice, nepojmenované nebo pojmenované. V určitém pořadí musí být zadány všechny poziční parametry a nelze je vynechat. Pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí. Poziční parametry jsou uvedeny jako první. Například tyto tři atributy jsou ekvivalentní:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

První parametr, název knihovny DLL, je pozice a vždy se nachází jako první; ostatní mají název. V takovém případě mají obě pojmenované parametry výchozí hodnotu false, takže je lze vynechat. Poziční parametry odpovídají parametrům konstruktoru atributu. Pojmenované nebo volitelné parametry odpovídají buď vlastnostem nebo polím atributu. Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.

### <a name="attribute-targets"></a>Cíle atributů

*Cíl* atributu je entita, na kterou se atribut vztahuje. Atribut může například platit pro třídu, konkrétní metodu nebo celé sestavení. Ve výchozím nastavení se atribut vztahuje na prvek, který následuje. Můžete ale také explicitně určit, zda je atribut použit na metodu, nebo na jeho parametr nebo na jeho návratovou hodnotu.

K explicitní identifikaci cíle atributu použijte následující syntaxi:

```csharp
[target : attribute-list]
```

Seznam možných `target` hodnot je uveden v následující tabulce.

|Cílová hodnota|Platí pro|
|------------------|----------------|
|`assembly`|Celé sestavení|
|`module`|Aktuální modul sestavení|
|`field`|Pole ve třídě nebo struktuře|
|`event`|Událost|
|`method`|`get` `set` Přístupové objekty metody nebo vlastnosti|
|`param`|Parametry metody nebo `set` parametry přístupového objektu vlastnosti|
|`property`|Vlastnost|
|`return`|Návratová hodnota metody, indexeru vlastností nebo `get` přistupujícího objektu vlastnosti|
|`type`|Struktura, třída, rozhraní, výčet nebo delegát|

Zadejte `field` cílovou hodnotu pro použití atributu pro pole zálohování vytvořené pro [automaticky implementovanou vlastnost](../../../properties.md).

Následující příklad ukazuje, jak použít atributy na sestavení a moduly. Další informace najdete v tématu [běžné atributy (C#)](../../../language-reference/attributes/global.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Následující příklad ukazuje, jak použít atributy na metody, parametry metody a návratové hodnoty metody v jazyce C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Bez ohledu na cíle `ValidatedContract` , které jsou definovány jako platné, je `return` nutné zadat cíl, a to i v případě, že `ValidatedContract` byly definovány pro použití pouze pro návratové hodnoty. Jinými slovy, kompilátor nebude používat `AttributeUsage` informace pro vyřešení dvojznačných cílů atributu. Další informace naleznete v tématu [AttributeUsage (C#)](../../../language-reference/attributes/general.md).

## <a name="common-uses-for-attributes"></a>Běžné použití atributů

Následující seznam obsahuje několik běžných použití atributů v kódu:

- Označení metod pomocí `WebMethod` atributu ve webových službách k označení toho, že by měla být metoda volat přes protokol SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.
- Popisuje způsob zařazení parametrů metody při spolupráci s nativním kódem. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Popisuje vlastnosti modelu COM pro třídy, metody a rozhraní.
- Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.
- Popisuje vaše sestavení s ohledem na název, verzi, popis nebo ochrannou známku.
- Popisuje, kteří členové třídy mají být serializováni k trvalému serializaci.
- Popisuje, jak mapovat mezi členy třídy a uzly XML pro serializaci kódu XML.
- Popisuje požadavky na zabezpečení pro metody.
- Určení vlastností používaných k vymáhání zabezpečení.
- Řízení optimalizace pomocí kompilátoru JIT (just-in-time), takže kód zůstane snadno laděn.
- Získání informací o volajícím metody.

## <a name="related-sections"></a>Související oddíly

Další informace najdete tady:

- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)  
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)  
- [Postup vytvoření sjednocení jazyka C/C++ pomocí atributů (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Společné atributy (C#)](../../../language-reference/attributes/global.md)  
- [Informace o volajícím (C#)](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../../index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Používání atributů v jazyce C #](../../../tutorials/attributes.md)
