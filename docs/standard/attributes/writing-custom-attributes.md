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
ms.openlocfilehash: d05df02bfc75e9aeb2c583a831bcee8b7b971206
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276126"
---
# <a name="writing-custom-attributes"></a>Zápis vlastních atributů
Chcete-li navrhnout vlastní atributy, nemusíte vytvářet hlavní spoustu nových konceptů. Pokud jste obeznámeni s objektově orientovaným programováním a víte, jak navrhovat třídy, již máte většinu potřebných znalostí. Vlastní atributy jsou v podstatě tradiční třídy, které jsou odvozeny přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType> . Stejně jako tradiční třídy obsahují vlastní atributy metody, které ukládají a načítají data.  
  
 Hlavní kroky pro správné navrhování vlastních tříd atributů jsou následující:  
  
- [Použití AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [Deklarace třídy atributů](#declaring-the-attribute-class)  
  
- [Deklarace konstruktorů](#declaring-constructors)  
  
- [Deklarace vlastností](#declaring-properties)  
  
 Tato část popisuje každý z těchto kroků a končí [příkladem vlastního atributu](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>Použití AttributeUsageAttribute  
 Deklarace vlastního atributu začíná na <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> , který definuje některé klíčové charakteristiky vaší třídy atributů. Můžete například určit, zda může být atribut děděn jinými třídami nebo určit, na které prvky lze atribut použít. Následující fragment kódu ukazuje, jak použít <xref:System.AttributeUsageAttribute> .  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute>Má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property)a [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>Člen AttributeTargets  
 V předchozím příkladu <xref:System.AttributeTargets.All?displayProperty=nameWithType> je určena, což značí, že tento atribut lze použít pro všechny prvky programu. Alternativně můžete určit <xref:System.AttributeTargets.Class?displayProperty=nameWithType> , že váš atribut lze použít pouze pro třídu, nebo <xref:System.AttributeTargets.Method?displayProperty=nameWithType> , což značí, že váš atribut lze použít pouze pro metodu. V tomto způsobu lze pomocí vlastního atributu označit všechny prvky programu jako popis.  
  
 Můžete také předat více <xref:System.AttributeTargets> hodnot. Následující fragment kódu určuje, že vlastní atribut lze použít pro libovolnou třídu nebo metodu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Zděděná vlastnost  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>Vlastnost označuje, zda lze atribut dědit pomocí tříd, které jsou odvozeny z tříd, pro které je použit atribut. Tato vlastnost používá buď `true` (výchozí), nebo `false` příznak. V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `true` , zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `false` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Tyto dva atributy jsou následně aplikovány na metodu v základní třídě `MyClass` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Nakonec `YourClass` je třída zděděna ze základní třídy `MyClass` . Metoda `MyMethod` ukazuje `MyAttribute` , ale ne `YourAttribute` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple – vlastnost  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType>Vlastnost určuje, zda více instancí atributu může existovat na elementu. Je-li nastavena na hodnotu `true` , je povolena více instancí. je-li nastavena na hodnotu `false` (výchozí možnost), je povolena pouze jedna instance.  
  
 V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.AllowMultiple%2A> hodnotu `false` , zatímco `YourAttribute` má hodnotu `true` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Při použití více instancí těchto atributů `MyAttribute` vytvoří kompilátor chybu. Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Pokud je <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost i <xref:System.AttributeUsageAttribute.Inherited%2A> vlastnost nastavena na hodnotu `true` , třída, která je zděděna z jiné třídy, může dědit atribut a mít v rámci stejné podřízené třídy použitu jinou instanci stejného atributu. Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je parametr nastaven na hodnotu `false` , hodnoty všech atributů v nadřazené třídě budou přepsány novými instancemi stejného atributu v podřízené třídě.  
  
## <a name="declaring-the-attribute-class"></a>Deklarace třídy atributů  
 Po použití <xref:System.AttributeUsageAttribute> můžete začít definovat specifiky vlastního atributu. Deklarace třídy atributu vypadá podobně jako deklarace tradiční třídy, jak je znázorněno v následujícím kódu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Tato definice atributu demonstruje následující body:  
  
- Třídy atributů musí být deklarovány jako veřejné třídy.  
  
- Podle konvence název třídy atributu končí **atributem**Word. I když se to nevyžaduje, doporučuje se tato konvence číst. Při použití atributu je zahrnutí atributu Word volitelné.  
  
- Všechny třídy atributů musí dědit přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType> .  
  
- V Microsoft Visual Basic musí mít všechny třídy vlastního atributu <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> atribut.  
  
## <a name="declaring-constructors"></a>Deklarace konstruktorů  
 Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy. Následující fragment kódu ilustruje typický konstruktor atributu. Tento veřejný konstruktor přijímá parametr a nastavuje členskou proměnnou rovnající se její hodnotě.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Můžete přetížit konstruktor pro přizpůsobení různých kombinací hodnot. Pokud definujete také [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vlastní třídu atributu, můžete při inicializaci atributu použít kombinaci pojmenovaných a pozičních parametrů. Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry jako pojmenované. V takovém případě nelze atribut inicializovat bez požadovaného parametru. Všechny ostatní parametry jsou volitelné. Všimněte si, že v Visual Basic konstruktory pro třídu atributu by neměly používat argument ParamArray.  
  
 Následující příklad kódu ukazuje, jak atribut, který používá předchozí konstruktor, lze použít pomocí volitelných a vyžadovaných parametrů. Předpokládá, že atribut má jednu požadovanou logickou hodnotu a jednu volitelnou vlastnost řetězce.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Deklarace vlastností  
 Pokud chcete definovat pojmenovaný parametr nebo poskytnout snadný způsob, jak vrátit hodnoty uložené v atributu, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Vlastnosti atributu by měly být deklarovány jako veřejné entity s popisem datového typu, který bude vrácen. Definujte proměnnou, která bude obsahovat hodnotu vlastnosti a přidružte ji k metodám **Get** a **set** . Následující příklad kódu ukazuje, jak implementovat jednoduchou vlastnost v atributu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Příklad vlastního atributu  
 Tato část obsahuje předchozí informace a ukazuje, jak navrhnout jednoduchý atribut, který dokumentuje informace o autorovi oddílu kódu. Atribut v tomto příkladu ukládá název a úroveň programátora a informaci o tom, zda byl kód zkontrolován. Používá tři soukromé proměnné pro uložení skutečných hodnot k uložení. Každá proměnná je reprezentovaná veřejnou vlastností, která získává a nastavuje hodnoty. Nakonec je definován konstruktor se dvěma požadovanými parametry.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Tento atribut lze použít pomocí úplného názvu, `DeveloperAttribute` nebo pomocí zkráceného názvu, `Developer` v jednom z následujících způsobů.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 První příklad ukazuje atribut použit pouze s požadovanými pojmenovanými parametry, zatímco druhý příklad ukazuje atribut použit s požadovaným i nepovinnými parametry.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Atributy](index.md)
