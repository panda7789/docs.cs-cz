---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: fe94f0ee778f14581fd7949f705cc22f12058b27
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="attributes-c"></a>Atributy (C#)

Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále). Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*. Další informace najdete v tématu [reflexe (C#)](../reflection.md).

Atributy mít následující vlastnosti:

- Atributy přidat metadata do programu. *Metadata* je informace o typech definované v programu. Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení. Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba. Další informace najdete v tématu, [vytváření vlastní atributy (C#)](creating-custom-attributes.md).
- Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.
- Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.
- Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe. Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Pomocí atributů

Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný. V jazyce C# zadejte atribut tím, že název atributu uzavřeny do hranatých závorek ([]) nad deklaraci entity, na který se vztahuje.

V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován jako v následujícím příkladu:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Více než jeden atribut je možné použít u deklaraci jako na následujícím příkladu:

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Některé atributy lze zadat více než jednou pro danou entitu. Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v na knihovny .NET. Však není potřeba zadejte příponu atribut při použití atributů v kódu. Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v knihovně tříd rozhraní .NET Framework.

### <a name="attribute-parameters"></a>Atribut parametry

Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem. Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat. Pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí. Nejprve jsou zadány poziční parametry. Například odpovídají tyto tři atributy:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem. V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat. Poziční parametry odpovídají parametry konstruktoru atributu. S názvem nebo volitelné parametry odpovídají vlastnosti nebo pole atributu. Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.

### <a name="attribute-targets"></a>Cíle atributů

*Cíl* atributu je ta entita, na které se vztahuje atribut. Atribut může například použít třídu, konkrétní metody nebo celé sestavení. Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází. Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.

K identifikaci explicitně atribut target, použijte následující syntaxi:

```csharp
[target : attribute-list]
```

Seznam možných `target` hodnoty je uvedené v následující tabulce.

|Hodnota cíle|Platí pro|
|------------------|----------------|
|`assembly`|Celý sestavení|
|`module`|Aktuální modul sestavení|
|`field`|Pole ve třídě nebo struktury|
|`event`|Událost|
|`method`|Metoda nebo `get` a `set` vlastnost přístupové objekty|
|`param`|Parametry metody nebo `set` parametry přistupující objekt vlastnosti|
|`property`|Vlastnost|
|`return`|Návratová hodnota metody, vlastnosti indexer nebo `get` přistupující objekt vlastnosti|
|`type`|Struktura, třídu, rozhraní, výčet nebo delegáta|

Chcete-li zadejte `field` hodnota cíle pro použití atributu na pole Základní vytvořili pro [automaticky implementované vlastnosti](../../../properties.md).

Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly. Další informace najdete v tématu [běžné atributy (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Následující příklad ukazuje, jak se má použít k metodám, metoda parametry, atributy a metoda návratové hodnoty v jazyce C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Bez ohledu na to cíle, na kterém `ValidatedContract` je definován jako platný, `return` cíl musí být zadaný, i když `ValidatedContract` byly definovány se provádí pouze návratové hodnoty. Jinými slovy, nebude používat kompilátor `AttributeUsage` informace týkající se řešení cíle nejednoznačný atributů. Další informace najdete v tématu [AttributeUsage (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Běžná použití atributů

Následující seznam obsahuje několik příkladů běžných použití atributů v kódu:

- Označení metody pomocí `WebMethod` atribut v webové služby k označení, že metoda by měla být s přes protokol SOAP. Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.
- Popisující, jak při vzájemné spolupráci s nativním kódem zařazování parametry metody. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Popisující COM vlastnosti tříd, metod a rozhraní.
- Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.
- Která popisují vaše sestavení z hlediska název, verze, popis nebo ochranná známka.
- Popisující, kteří členové třídy k serializaci trvalosti.
- Popisující, jak pro mapování mezi členy třídy a z uzlů XML pro serializaci XML.
- Popisuje požadavky na zabezpečení pro metody.
- Zadání vlastnosti slouží k vynucení zabezpečení.
- Řízení optimalizace kompilátorem v běhu (JIT), takže stále snadno ladit kód.
- Získání informací o volajícího, aby metoda.

## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)  
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)  
- [Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Mezi běžné atributy (C#)](common-attributes.md)  
- [Informace o subjektu volajícím (C#)](../caller-information.md)  

## <a name="see-also"></a>Viz také

 [Průvodce programováním v jazyce C#](../../index.md)  
 [Reflexe (C#)](../reflection.md)  
 [Atributy](../../../../standard/attributes/index.md)  
 [Pomocí atributů v jazyce C#](../../../tutorials/attributes.md)  
