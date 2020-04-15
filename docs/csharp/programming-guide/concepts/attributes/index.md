---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 62424163303417746a67707d9ef34185954db316
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389544"
---
# <a name="attributes-c"></a>Atributy (C#)

Atributy poskytují výkonnou metodu připojování metadat nebo deklarativních informací s kódem (sestavení, typy, metody, vlastnosti atd.). Poté, co je atribut přidružen k entitě programu, může být tento atribut dotazován za běhu pomocí techniky nazývané *reflexe*. Další informace naleznete v [tématu Reflection (C#)](../reflection.md).

Atributy mají následující vlastnosti:

- Atributy přidávají do programu metadata. *Metadata* jsou informace o typech definovaných v programu. Všechna sestavení rozhraní .NET obsahují zadanou sadu metadat, která popisuje typy a členy typu definované v sestavení. Můžete přidat vlastní atributy a zadat další informace, které jsou požadovány. Další informace naleznete v [tématu Vytváření vlastních atributů (C#).](creating-custom-attributes.md)
- Jeden nebo více atributů můžete použít na celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.
- Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.
- Program může zkoumat vlastní metadata nebo metadata v jiných programech pomocí reflexe. Další informace naleznete [v tématu Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Použití atributů

Atributy lze umístit na většinu jakékoli prohlášení, i když konkrétní atribut může omezit typy deklarací, na kterých je platný. V c# zadáte atribut umístěním názvu atributu uzavřeného v hranatých závorkách ([]) nad deklaraci entity, na kterou se vztahuje.

V tomto příkladu <xref:System.SerializableAttribute> se atribut používá k použití určité charakteristiky na třídu:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována jako následující příklad:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Více než jeden atribut lze umístit na prohlášení, jak ukazuje následující příklad:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Některé atributy lze zadat více než jednou pro danou entitu. Příkladem takového víceúčelového atributu je <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Podle konvence všechny názvy atributů končí slovem "Atribut", aby se odlišily od ostatních položek v knihovnách .NET. Při použití atributů v kódu však není nutné zadávat příponu atributu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, `DllImportAttribute` ale je skutečný název atributu v knihovně tříd rozhraní .NET Framework.

### <a name="attribute-parameters"></a>Parametry atributů

Mnoho atributů má parametry, které mohou být poziční, nepojmenované nebo pojmenované. Všechny poziční parametry musí být zadány v určitém pořadí a nelze je vynechat. Pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí. Nejprve jsou zadány poziční parametry. Například tyto tři atributy jsou ekvivalentní:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

První parametr, název dll, je poziční a vždy je na prvním místě; ostatní jsou pojmenovány. V tomto případě oba pojmenované parametry výchozí false, takže mohou být vynechány. Poziční parametry odpovídají parametrům konstruktoru atributu. Pojmenované nebo volitelné parametry odpovídají vlastnostem nebo polím atributu. Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.

### <a name="attribute-targets"></a>Cíle atributů

*Cílem* atributu je entita, na kterou se atribut vztahuje. Atribut může například použít pro třídu, určitou metodu nebo celé sestavení. Ve výchozím nastavení se atribut vztahuje na prvek, který za ním následuje. Můžete však také explicitně určit, například zda je atribut použit pro metodu nebo její parametr nebo na jeho vrácenou hodnotu.

Chcete-li explicitně identifikovat cíl atributu, použijte následující syntaxi:

```csharp
[target : attribute-list]
```

Seznam možných `target` hodnot je uveden v následující tabulce.

|Cílová hodnota|Platí pro|
|------------------|----------------|
|`assembly`|Celá sestava|
|`module`|Aktuální montážní modul|
|`field`|Pole ve třídě nebo struktuře|
|`event`|Událost|
|`method`|Přístupové `get` `set` objekty metody nebo vlastnosti|
|`param`|Parametry metody `set` nebo parametry přístupového objektu vlastnosti|
|`property`|Vlastnost|
|`return`|Vrácená hodnota metody, indexeru `get` vlastností nebo přistupujícího objektu vlastností|
|`type`|Struktura, třída, rozhraní, výčt nebo delegát|

Zadali byste `field` cílovou hodnotu, která má atribut použít na záložní pole vytvořené pro [automaticky implementovanou vlastnost](../../../properties.md).

Následující příklad ukazuje, jak použít atributy sestavení a modulů. Další informace naleznete [v tématu Common Attributes (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Následující příklad ukazuje, jak použít atributy metody, parametry metody a metody vrácené hodnoty v C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Bez ohledu na cíle, na kterých `ValidatedContract` `return` je definována jako platná, cíl musí být určen, i když `ValidatedContract` byly definovány použít pouze pro vrácené hodnoty. Jinými slovy kompilátor nebude `AttributeUsage` používat informace k vyřešení nejednoznačných cílů atributů. Další informace naleznete v tématu [AttributeUsage (C#)](../../../language-reference/attributes/general.md).

## <a name="common-uses-for-attributes"></a>Běžné použití atributů

Následující seznam obsahuje několik běžných použití atributů v kódu:

- Metody označení `WebMethod` pomocí atributu ve webových službách označují, že metoda by měla být volatelná přes protokol SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.
- Popisující, jak zařazovat parametry metody při spolupráci s nativním kódem. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Popisující vlastnosti com pro třídy, metody a rozhraní.
- Volání nespravovaného <xref:System.Runtime.InteropServices.DllImportAttribute> kódu pomocí třídy.
- Popis vašeho sestavení z hlediska názvu, verze, popisu nebo ochranné známky.
- Popisující, které členy třídy serializovat pro trvalost.
- Popis mapování mezi členy třídy a uzly XML pro serializaci XML.
- Popisující požadavky na zabezpečení metod.
- Určení charakteristik používaných k vynucení zabezpečení.
- Řízení optimalizace kompilátorem just-in-time (JIT), takže kód zůstává snadno ladit.
- Získání informací o volajícím na metodu.

## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)  
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)  
- [Jak vytvořit sjednocení C/C++ pomocí atributů (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Běžné atributy (C#)](common-attributes.md)  
- [Informace o volajícím (C#)](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../../index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Použití atributů v C #](../../../tutorials/attributes.md)
