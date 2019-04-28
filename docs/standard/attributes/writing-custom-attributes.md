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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d0a0659c99a49770d0d08460026363ecef06654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698955"
---
# <a name="writing-custom-attributes"></a>Zápis vlastních atributů
Návrh vlastní atributy, není potřeba hlavní mnoho nových konceptů. Pokud jste obeznámeni s objektově orientované programování a vědět, jak do návrhu tříd, již máte většinu znalosti potřebné. Uživatelských atributů, které jsou v podstatě tradiční třídy, které jsou přímo nebo nepřímo odvozeny z <xref:System.Attribute?displayProperty=nameWithType>. Stejně jako tradiční třídy uživatelských atributů, které obsahují metody, které ukládají a načítají data.  
  
 Hlavní kroky správně návrh vlastního atributu třídy jsou následující:  
  
- [Použití AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [Deklarace třídy atributů](#declaring-the-attribute-class)  
  
- [Deklarování konstruktorů](#declaring-constructors)  
  
- [Deklarování vlastností](#declaring-properties)  
  
 Tato část popisuje jednotlivé kroky a končí [příklad vlastního atributu](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>Použití AttributeUsageAttribute  
 Vlastní atribut deklarace začíná <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, která definuje některé klíčové vlastnosti třídy atributu. Můžete například určit, zda atribut může být zděděny jiné třídy nebo prvky, které atribut lze použít k určení. Následující fragment kódu ukazuje, jak používat <xref:System.AttributeUsageAttribute>.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute> Má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#attributetargets-member), [zděděné](#inherited-property), a [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>AttributeTargets – člen  
 V předchozím příkladu <xref:System.AttributeTargets.All?displayProperty=nameWithType> není zadána, která udává, že tento atribut lze použít na všechny prvky programu. Alternativně můžete zadat <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, označující, že atribut lze použít pouze pro třídy, nebo <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, označující, že atribut lze použít pouze pro metodu. Všechny prvky programu může být označený pro popis vlastní atribut tímto způsobem.  
  
 Můžete také předat více <xref:System.AttributeTargets> hodnoty. Následující fragment kódu určuje, že vlastní atribut lze použít na libovolné třídy nebo metody.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Zděděná vlastnost  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Vlastnost určuje, zda atribut může dědit třídy, které jsou odvozeny z tříd, do kterých je použit atribut. Tato vlastnost má buď `true` (výchozí) nebo `false` příznak. V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `true`, zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `false`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Dva atributy se následně použijí na metodu v základní třídě `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Nakonec třídy `YourClass` se dědí ze základní třídy `MyClass`. Metoda `MyMethod` ukazuje `MyAttribute`, ale ne `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple – vlastnost  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Vlastnost určuje, zda může existovat více instancí atributu na elementu. Pokud hodnotu `true`, je povoleno více instancí; Pokud nastavena na `false` (výchozí), je povolena pouze jedna instance.  
  
 V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.AllowMultiple%2A> hodnotu `false`, zatímco `YourAttribute` má hodnotu `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Při použití několika instancí těchto atributů, `MyAttribute` způsobí chybu kompilátoru. Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost a <xref:System.AttributeUsageAttribute.Inherited%2A> nastavenou na `true`, třídu, která pochází z jiné třídy můžete dědit atribut a jiná instance stejné použije ve stejné třídě podřízené. Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je nastavena na `false`, hodnoty atributů v nadřazené třídě budou přepsány instalací nových instancí stejný atribut v podřízené třídy.  
  
## <a name="declaring-the-attribute-class"></a>Deklarace třídy atributů  
 Po instalaci <xref:System.AttributeUsageAttribute>, můžete začít definovat, jaké jsou specifikace atributu. Deklarace třídy atributu vypadá podobně jako deklaraci tradiční třídy, jak je ukázáno v následujícím kódu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Tato definice atributu demonstruje následující body:  
  
- Třídy atributů musí být deklarována jako veřejné třídy.  
  
- Podle konvence, název třídy atributu končí slovem **atribut**. Přestože se nevyžaduje, doporučuje se tato konvence pro lepší čitelnost. Při použití atribut zahrnutí slovo atribut je volitelný.  
  
- Všechny třídy atributů musí dědit přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType>.  
  
- Microsoft Visual Basic, musí mít všechny vlastní třídy atributu <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> atribut.  
  
## <a name="declaring-constructors"></a>Deklarování konstruktorů  
 Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy. Následující fragment kódu ukazuje typický konstruktor atributu. Tento veřejný konstruktor přijímá parametr a nastaví členskou proměnnou na hodnotu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Můžete použít přetížení konstruktoru pro různé kombinace hodnot. Pokud můžete také definujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vaši vlastní třídu atributu, můžete použít kombinaci pojmenované a poziční parametry, při inicializaci atributu. Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry jako s názvem. V takovém případě atribut nelze inicializovat bez povinný parametr. Všechny ostatní parametry jsou volitelné. Všimněte si, že v jazyce Visual Basic by neměly používat konstruktory pro třídy atributu ParamArray argument.  
  
 Následující příklad kódu ukazuje, jak atribut, který se používá, že předchozí konstruktor lze použít pomocí povinných a volitelných parametrů. Předpokládá, že atribut má jeden povinný logickou hodnotu a vlastnost jeden volitelný řetězec.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Deklarování vlastností  
 Pokud chcete definovat parametr s názvem nebo poskytují snadný způsob, jak vrátit hodnoty uložené ve vašem atributu, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Vlastnosti atributu by měl být deklarován jako veřejné entit s popisem datového typu, který bude vrácen. Definujte proměnné, která bude obsahovat hodnotu vlastnosti vaší a přidružte jej k **získat** a **nastavit** metody. Následující příklad kódu ukazuje, jak implementovat jednoduché vlastnosti v atributu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Příklad vlastního atributu  
 Tato část zahrnuje předchozí informace a ukazuje, jak navrhovat jednoduché atributy, které dokumenty informace o autorovi část kódu. Atribut v tomto příkladu obsahuje název a úroveň programátora, a určuje, zda kód revidovaný. Používá tři soukromé proměnné k ukládání skutečné hodnoty uložte. Každá proměnná je reprezentován veřejnou vlastnost, která získá a nastaví hodnoty. Nakonec je konstruktor definován s dvěma požadovanými parametry.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Můžete použít tento atribut, pomocí úplného názvu `DeveloperAttribute`, nebo pomocí zkrácený název `Developer`, v jednom z následujících způsobů.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 První příklad ukazuje, použije se pouze požadované pojmenované parametry, zatímco druhý příklad ukazuje atribut s povinných a volitelných parametrů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Atributy](../../../docs/standard/attributes/index.md)
