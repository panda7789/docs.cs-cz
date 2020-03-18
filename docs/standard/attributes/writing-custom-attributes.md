---
title: Zápis vlastních atributů
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140583"
---
# <a name="writing-custom-attributes"></a>Zápis vlastních atributů
Chcete-li navrhnout vlastní atributy, není nutné zvládnout mnoho nových konceptů. Pokud jste obeznámeni s objektově orientované programování a víte, jak navrhnout třídy, již máte většinu znalostí potřebných. Vlastní atributy jsou v podstatě tradiční <xref:System.Attribute?displayProperty=nameWithType>třídy, které jsou odvozeny přímo nebo nepřímo z . Stejně jako tradiční třídy, vlastní atributy obsahují metody, které ukládají a načítají data.  
  
 Primární kroky správně navrhnout vlastní atribut třídy jsou následující:  
  
- [Použití atributu AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [Deklarování třídy atributu](#declaring-the-attribute-class)  
  
- [Deklarování konstruktorů](#declaring-constructors)  
  
- [Deklarování vlastností](#declaring-properties)  
  
 Tato část popisuje každý z těchto kroků a končí [s příkladem vlastní atribut](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>Použití atributu AttributeUsageAttribute  
 Deklarace vlastního atributu <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>začíná na , který definuje některé klíčové charakteristiky třídy atributů. Můžete například určit, zda může být váš atribut zděděn jinými třídami, nebo určit, na které prvky lze atribut použít. Následující fragment kódu ukazuje, jak <xref:System.AttributeUsageAttribute>používat .  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 Má <xref:System.AttributeUsageAttribute> tři členy, které jsou důležité pro vytvoření vlastníatributy: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), a [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>Člen attributetargets  
 V předchozím příkladu <xref:System.AttributeTargets.All?displayProperty=nameWithType> je zadán, označující, že tento atribut lze použít na všechny prvky programu. Případně můžete zadat <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, označující, že váš atribut lze použít <xref:System.AttributeTargets.Method?displayProperty=nameWithType>pouze pro třídu, nebo , označující, že atribut lze použít pouze pro metodu. Všechny prvky programu mohou být označeny pro popis vlastním atributem tímto způsobem.  
  
 Můžete také předat <xref:System.AttributeTargets> více hodnot. Následující fragment kódu určuje, že vlastní atribut lze použít pro libovolnou třídu nebo metodu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Zděděná vlastnost  
 Vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> označuje, zda váš atribut může být zděděn třídy, které jsou odvozeny z tříd, na které je atribut použit. Tato vlastnost trvá `true` buď (výchozí) nebo `false` příznak. V následujícím `MyAttribute` příkladu má <xref:System.AttributeUsageAttribute.Inherited%2A> výchozí `true`hodnotu , zatímco `YourAttribute` má hodnotu <xref:System.AttributeUsageAttribute.Inherited%2A> `false`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Tyto dva atributy jsou pak použity `MyClass`na metodu v základní třídě .  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Nakonec je `YourClass` třída zděděna `MyClass`ze základní třídy . Metoda `MyMethod` ukazuje `MyAttribute`, `YourAttribute`ale ne .  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>Vlastnost Povolit více  
 Vlastnost <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> označuje, zda může existovat více instancí atributu na elementu. Pokud je `true`nastavena na , jsou povoleny více instancí; pokud je `false` nastavena na (výchozí), je povolena pouze jedna instance.  
  
 V `MyAttribute` následujícím příkladu má <xref:System.AttributeUsageAttribute.AllowMultiple%2A> výchozí `false`hodnotu , zatímco `YourAttribute` má hodnotu `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Při použití více instancí těchto `MyAttribute` atributů, vytvoří chybu kompilátoru. Následující příklad kódu ukazuje platné `YourAttribute` použití a `MyAttribute`neplatné použití .  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Pokud jsou <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A> i vlastnost `true`nastaveny na , třída, která je zděděna z jiné třídy, může zdědit atribut a mít jinou instanci stejného atributu použitou ve stejné podřízené třídě. Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je `false`nastavena na , hodnoty všechny atributy v nadřazené třídě budou přepsány nové instance stejného atributu v podřízené třídě.  
  
## <a name="declaring-the-attribute-class"></a>Deklarování třídy atributů  
 Po použití <xref:System.AttributeUsageAttribute>aplikace můžete začít definovat specifika atributu. Deklarace třídy atributů vypadá podobně jako deklarace tradiční třídy, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Tato definice atributu ukazuje následující body:  
  
- Třídy atributů musí být deklarovány jako veřejné třídy.  
  
- Podle konvence název třídy atributu končí slovem **Atribut**. I když není vyžadováno, tato konvence se doporučuje pro čitelnost. Při použití atributu je zahrnutí slova Atribut volitelné.  
  
- Všechny třídy atributů musí <xref:System.Attribute?displayProperty=nameWithType>dědit přímo nebo nepřímo z .  
  
- V jazyce Microsoft Visual Basic musí <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> mít atribut všechny třídy vlastních atributů.  
  
## <a name="declaring-constructors"></a>Deklarování konstruktorů  
 Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy. Následující fragment kódu ilustruje konstruktor typického atributu. Tento veřejný konstruktor převezme parametr a nastaví člennou proměnnou rovnou jeho hodnotě.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Můžete přetížení konstruktoru tak, aby vyhovovaly různé kombinace hodnot. Pokud také definujete [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vlastní třídu atributů, můžete při inicializaci atributu použít kombinaci pojmenovaných a pozičních parametrů. Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry, jak je pojmenováno. V tomto případě nelze atribut inicializovat bez požadovaného parametru. Všechny ostatní parametry jsou volitelné. Všimněte si, že v jazyce Visual Basic by konstruktory pro třídu atributů neměly používat argument ParamArray.  
  
 Následující příklad kódu ukazuje, jak lze použít atribut, který používá předchozí konstruktor pomocí volitelných a požadovaných parametrů. Předpokládá, že atribut má jednu požadovanou logickou hodnotu a jednu volitelnou vlastnost řetězce.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Deklarování vlastností  
 Pokud chcete definovat pojmenovaný parametr nebo poskytnout snadný způsob, jak vrátit hodnoty uložené atributem, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Vlastnosti atributu by měly být deklarovány jako veřejné entity s popisem datového typu, který bude vrácen. Definujte proměnnou, která bude obsahovat hodnotu vaší vlastnosti, a přidružte ji k metodám **get** a **set.** Následující příklad kódu ukazuje, jak implementovat jednoduchou vlastnost ve vašem atributu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Příklad vlastního atributu  
 Tato část obsahuje předchozí informace a ukazuje, jak navrhnout jednoduchý atribut, který dokumentuje informace o autorovi části kódu. Atribut v tomto příkladu ukládá název a úroveň programátora a zda byl kód zkontrolován. Používá tři soukromé proměnné pro uložení skutečné hodnoty uložit. Každá proměnná je reprezentována veřejnou vlastností, která získá a nastaví hodnoty. Nakonec je konstruktor definován dvěma požadovanými parametry.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Tento atribut můžete použít pomocí `DeveloperAttribute`celého názvu , nebo pomocí `Developer`zkráceného názvu , jedním z následujících způsobů.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 První příklad ukazuje atribut použitý pouze s požadovanými pojmenovanými parametry, zatímco druhý příklad ukazuje atribut použitý s požadovanými i volitelnými parametry.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Atributy](../../../docs/standard/attributes/index.md)
