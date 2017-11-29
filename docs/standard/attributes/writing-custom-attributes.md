---
title: "Zápis vlastních atributů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a>Zápis vlastních atributů
K návrhu vlastní atributy, není potřeba hlavní mnoho nových konceptů. Pokud jste obeznámeni s objektově orientované programování a vědět, jak navrhnout třídy, že máte většinu potřebných znalostí. Vlastní atributy jsou v podstatě tradiční třídy, které jsou odvozeny od přímo nebo nepřímo <xref:System.Attribute?displayProperty=nameWithType>. Stejně jako tradiční třídy vlastní atributy obsahují metody, které ukládají a načítají data.  
  
 Hlavní kroky správně návrhu vlastní atribut třídy jsou následující:  
  
-   [Použití AttributeUsageAttribute](#cpconapplyingattributeusageattribute)  
  
-   [Deklarování třídy atributů](#cpcondeclaringattributeclass)  
  
-   [Deklarování konstruktorů](#cpcondeclaringconstructors)  
  
-   [Deklarování vlastností](#cpcondeclaringproperties)  
  
 Tato část popisuje každý z těchto kroků a končí [příklad vlastní atribut](#cpconcustomattributeexample).  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a>Použití AttributeUsageAttribute  
 Vlastní atribut deklarace začíná **AttributeUsageAttribute**, která definuje některé klíčové charakteristiky vaší třídy atributů. Můžete například určit, zda vaše atribut možné zdědit jiné třídy, nebo zadejte prvky, které atribut lze použít k. Následující fragment kódu ukazuje, jak používat **AttributeUsageAttribute**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#cpconwritingcustomattributesanchor1), [zděděné](#cpconwritingcustomattributesanchor2), a [AllowMultiple](#cpconwritingcustomattributesanchor3).  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a>Člen AttributeTargets  
 V předchozím příkladu **AttributeTargets.All** není zadaný, označující, že tento atribut lze použít pro všechny prvky programu. Alternativně můžete zadat **AttributeTargets.Class**, označující, že váš atribut lze použít pouze na třídu, nebo **AttributeTargets.Method**, označující, že můžete použít atribut pouze pro metodu. Všechny elementy program může být označen pro popis vlastní atribut tímto způsobem.  
  
 Můžete také předat více instancí <xref:System.AttributeTargets>. Následující fragment kódu určuje, že vlastních atributů může být použitá pro všechny třída nebo metoda.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a>Zděděná vlastnost  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Vlastnost určuje, zda požadovaný atribut může být zděděn třídy, které jsou odvozeny od třídy, na které je použit požadovaný atribut. Tato vlastnost má buď **true** (výchozí) nebo **false** příznak. Například v následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu **true**, zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Dva atributy jsou poté použity na metodu v základní třídě `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Nakonec je třída `YourClass` je zděděn ze základní třídy `MyClass`. Metoda `MyMethod` ukazuje `MyAttribute`, ale ne `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a>AllowMultiple – vlastnost  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Vlastnost určuje, zda může existovat více instancí atributu v elementu. Pokud nastavena na **true**, více instance jsou povoleny; Pokud nastavena na **false** (výchozí), je povolena pouze jedna instance.  
  
 V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.AllowMultiple%2A> hodnotu **false**, zatímco `YourAttribute` má hodnotu **true**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Pokud jsou použity více instancí těchto atributů, `MyAttribute` dojde k chybě kompilátoru. Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost a <xref:System.AttributeUsageAttribute.Inherited%2A> nastavena na **true**, třídu, která dědí z jiné třídy lze dědit atribut a mít jiná instance stejného atributu použité ve stejné třídě podřízené. Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je nastaven na **false**, hodnoty atributů v nadřazené třídě budou přepsány nové instance třídy stejný atribut ve třídě podřízené.  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a>Deklarování třídy atributů  
 Po použití <xref:System.AttributeUsageAttribute>, můžete začít definovat specifické požadovaný atribut. Deklarace třídy atributu bude vypadat podobně jako deklarace tradiční třídy, jak je ukázáno v následujícím kódu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Tato definice atributu ukazuje následující body:  
  
-   Jako veřejné třídy musí být deklarován atribut třídy.  
  
-   Podle konvence, název třídy atributů končí slovem **atribut**. Není požadováno touto konvencí se doporučuje čitelnější. Při použití atribut zahrnutí aplikace word atribut je volitelný.  
  
-   Všechny třídy atributu musí dědit přímo nebo nepřímo z **System.Attribute**.  
  
-   V jazyce Microsoft Visual Basic, musí mít všechny vlastní atribut třídy **AttributeUsageAttribute** atribut.  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a>Deklarování konstruktorů  
 Atributy jsou inicializovány konstruktory stejným způsobem jako tradiční třídy. Následující fragment kódu ukazuje typický konstruktor atributu. Tento konstruktor public, který přebírá parametr a nastaví její hodnota rovna členské proměnné.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Můžete použít přetížení konstruktoru pro různé kombinace hodnot. Pokud je také definovat [vlastnost](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) pro vaše vlastní atribut třídu, můžete použít kombinaci s názvem a pojmenovaných parametrů při inicializaci atributu. Obvykle můžete definovat všechny požadované parametry jako poziční a všechny volitelné parametry jako s názvem. V takovém případě atribut nelze inicializovat bez povinný parametr. Všechny ostatní parametry jsou volitelné. Upozorňujeme, že v jazyce Visual Basic konstruktory pro třídu atributu nesmí použít ParamArray argument.  
  
 Následující příklad kódu ukazuje, jak atribut, který používá předchozí konstruktor lze aplikovat pomocí volitelné a požadované parametry. Přitom se předpokládá, že má atribut vyžaduje jednu logickou hodnotu a vlastnost jeden volitelný řetězec.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a>Deklarování vlastností  
 Pokud chcete definovat pojmenovaný parametr nebo poskytují snadný způsob, jak vrátit hodnoty uložených ve vašem atributu, deklarovat [vlastnost](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Vlastnosti atributu by měla deklarovat jako veřejné entity s popisem datového typu, který bude vrácen. Definujte proměnnou, která bude obsahovat hodnotu vaší vlastnosti a přidružit ho s **získat** a **nastavit** metody. Následující příklad kódu ukazuje, jak implementovat jednoduché vlastnosti ve vašem atributu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a>Příklad vlastní atribut  
 Tato část zahrnuje předchozí informace a ukazuje, jak navrhnout jednoduché atributy, které dokumentů informace o autorovi oddílu kódu. Atribut v tomto příkladu obsahuje název a úrovně programátory, a jestli byl revidován kód. Tři soukromé proměnné používá k ukládání skutečnými hodnotami pro uložení. Každá proměnná je reprezentována veřejné vlastnosti, který získá a nastaví hodnoty. Nakonec konstruktoru je definována pomocí dvou požadované parametry.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Můžete použít tento atribut pomocí úplný název, `DeveloperAttribute`, nebo pomocí zkrácený název `Developer`, v jednom z následujících způsobů.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 V prvním příkladu ukazuje atribut obsahuje jenom požadované pojmenované parametry, zatímco druhý příklad ukazuje atribut s povinných a volitelných parametrů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [Atributy](../../../docs/standard/attributes/index.md)
