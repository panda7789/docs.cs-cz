---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: f211e8af48bdfef0bb9bf4341c7a5911b5695101
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573339"
---
# <a name="attributes-c"></a>Atributy (C#)

Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále). Po atributu je spojen s entitou program, atribut může být dotázán za běhu pomocí techniky označované jako *reflexe*. Další informace najdete v tématu [reflexe (C#)](../reflection.md).

Atributy mají následující vlastnosti:

- Atributy přidat metadata do programu. *Metadata* obsahuje informace o typy definované v programu. Všechna sestavení rozhraní .NET obsahují zadanou množinu metadata popisující typy a členy typu definované v sestavení. Můžete přidat vlastní atributy k jakékoli další informace, které je nutné zadat. Další informace najdete v tématu, [vytváření vlastních atributů (C#)](creating-custom-attributes.md).
- Můžete použít jeden nebo více atributů na celé sestavení, moduly nebo menší prvky programu, jako například třídy a vlastnosti.
- Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.
- Aplikace můžete zkontrolovat svou vlastní metadaty nebo metadaty v jiných aplikacích pomocí reflexe. Další informace najdete v tématu [přístup k atributy podle použití reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Pomocí atributů

Atributy je možné použít u libovolného deklarace, když konkrétního atributu můžete narazit na omezení typů deklarace, na kterých je platný. V C#, atribut určíte tak, že název atributu uzavřeny do hranatých závorek ([]) nad deklarací entit, ke kterému se vztahuje.

V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování konkrétní charakteristiku pro třídu:

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metodu s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován jako v následujícím příkladu:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Více než jeden atribut je možné použít v deklaraci jako v následujícím příkladu:

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Některé atributy můžete zadat více než jednou pro danou entitu. Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Podle konvence končí všechny názvy atributů slovem "Atribut", abychom je odlišili od ostatních položek v knihovny .NET. Ale není potřeba zadat atribut přípon při použití atributů v kódu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v knihovně tříd rozhraní .NET Framework.

### <a name="attribute-parameters"></a>Atribut parametrů

Mnoho atributů mít parametry, které mohou být poziční, nepojmenovaný nebo s názvem. Žádné poziční parametry musí být zadán v určitém pořadí a nelze jej vynechat. Pojmenované parametry jsou volitelné a dá se zadat v libovolném pořadí. Poziční parametry jsou zadán jako první. Například tyto tři atributy jsou ekvivalentní:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

První parametr, název knihovny DLL je poziční a dodává se vždycky první; ostatní jsou pojmenovány. V takovém případě pojmenované výchozí parametry na hodnotu false, takže lze vynechat. Poziční parametry odpovídají parametry konstruktoru atributu. Pojmenované a nepovinné parametry odpovídají vlastnosti nebo pole atributu. V dokumentaci jednotlivých atributů informace o výchozí hodnoty parametrů.

### <a name="attribute-targets"></a>Cíle atributů

*Cílové* atributu je entita, ke kterému se vztahuje atribut. Atribut může například použít pro třídu, konkrétní metody nebo celé sestavení. Ve výchozím nastavení atribut se vztahuje k elementu, který předchází. Ale můžete také explicitně identifikovat, například zda atributu se použije k metodě, její parametr nebo na jeho návratovou hodnotu.

Cíl atributu explicitně identifikovat, použijte následující syntaxi:

```csharp
[target : attribute-list]
```

Seznam možných `target` hodnot je uveden v následující tabulce.

|Cílová hodnota|Platí pro|
|------------------|----------------|
|`assembly`|Celé sestavení|
|`module`|Aktuální modul sestavení|
|`field`|Pole třídy nebo struktury|
|`event`|Událost|
|`method`|Metoda nebo `get` a `set` přistupující objekty vlastnosti|
|`param`|Parametry metody nebo `set` parametry přistupující objekt vlastnosti|
|`property`|Vlastnost|
|`return`|Návratová hodnota metody, vlastnosti indexeru nebo `get` přistupující objekt vlastnosti|
|`type`|Struktury, třídy, interface, enum nebo delegate|

Zadejte `field` cílovou hodnotu použijte atribut na pomocné pole vytvoří pro [automaticky implementované vlastnosti](../../../properties.md).

Následující příklad ukazuje způsob použití atributů pro sestavení a modulů. Další informace najdete v tématu [běžné atributy (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Následující příklad ukazuje způsob použití atributů pro metody, parametry metody a metody návratové hodnoty v jazyce C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Bez ohledu na to cíle, na kterém `ValidatedContract` je definován jako platný, `return` cíl musí být zadaný, i v případě `ValidatedContract` byly definovány bylo použito pouze na návratové hodnoty. Jinými slovy, nebudeme je používat kompilátor `AttributeUsage` informace k jejímu vyřešení nejednoznačný atribut cíle. Další informace najdete v tématu [AttributeUsage (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Běžné použití atributů

Následující seznam obsahuje několik běžných použití atributů v kódu:

- Označení metody pomocí `WebMethod` atribut ve webové služby k označení, že metoda mělo by být umožněno prostřednictvím protokolu SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.
- Popis způsobu zařazení parametrů metody při vzájemné spolupráci s nativním kódem. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Popis vlastnosti modelu COM pro třídy, metody a rozhraní.
- Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.
- Popisující vaše sestavení z hlediska název, verze, popis nebo ochranná známka.
- Popisující, které členy třídy k serializaci trvalosti.
- Popisující způsob, jakým mapování mezi členy třídy a z uzlů XML pro serializaci kódu XML.
- Popisuje požadavky zabezpečení pro metody.
- Zadání vlastnosti používá k vynucení zabezpečení.
- Řízení optimalizace kompilátoru just-in-time (JIT), tak zůstane usnadňuje ladění kódu.
- Získání informací o volajícím metody.

## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)  
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)  
- [Postupy: Vytváření sjednocení C/C++ pomocí atributů (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Běžné atributy (C#)](common-attributes.md)  
- [Informace o volajícím (C#)](../caller-information.md)  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Použití atributů v jazyce C#](../../../tutorials/attributes.md)
