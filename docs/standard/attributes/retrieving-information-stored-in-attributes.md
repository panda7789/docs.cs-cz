---
title: Načítání informací uložených v atributech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b6799763b4635632728561eef2820b26820aeed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570396"
---
# <a name="retrieving-information-stored-in-attributes"></a>Načítání informací uložených v atributech
Načítání vlastní atribut je jednoduchý proces. Nejprve deklarujte instanci atribut, který chcete načíst. Potom použít <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metoda pro inicializaci nového atributu na hodnotu atributu, který chcete načíst. Jakmile nový atribut inicializován, jednoduše použijte jeho vlastnosti a získat hodnoty.  
  
> [!IMPORTANT]
>  Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění. Chcete-li načíst atributy pro kód načtený do kontextu pouze pro reflexi, musíte použít <xref:System.Reflection.CustomAttributeData> třídy, jak je znázorněno v [postupy: načtení sestavení do kontextu Reflection](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Tato část popisuje tyto způsoby načíst atributy:  
  
-   [Načítání jednu instanci atributu](#cpconretrievingsingleinstanceofattribute)  
  
-   [Načítání více instancí atributu použitého pro stejný obor](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Načítání více instancí atributu použitého pro různé obory](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Načítání jednu instanci atributu  
 V následujícím příkladu `DeveloperAttribute` (popsané v předchozí části) se použijí na `MainApp` třídy na úrovni třídy. `GetAttribute` Používá metoda **GetCustomAttribute** načíst hodnotami uloženými v `DeveloperAttribute` na úrovni třídy před jejich zobrazením ke konzole.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Tento program zobrazí následující text při spuštění.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Pokud není nalezen atribut, **GetCustomAttribute** metoda inicializuje `MyAttribute` na hodnotu null. Tento příklad zkontroluje `MyAttribute` takovýchto instancí a upozorní uživatele, pokud není nalezen žádný atribut. Pokud `DeveloperAttribute` nebyla nalezena v oboru třída konzoli se zobrazí následující zprávu.  
  
```  
The attribute was not found.   
```  
  
 Tento příklad předpokládá, že definice atributu je v aktuálním oboru názvů. Nezapomeňte importovat obor názvů, ve kterém se nachází definice atributu, pokud není v aktuálním oboru názvů.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Načítání více instancí atributu použitého pro stejný obor  
 V předchozím příkladu třída ke kontrole a konkrétní atribut se předávají do <xref:System.Attribute.GetCustomAttribute%2A>. Tento kód funguje dobře, pokud pouze jedna instance atributu se použije na úrovni třídy. Ale v případě, že jsou na stejné úrovni třídy, použito více instancí atributu **GetCustomAttribute** metoda nenačte všechny informace. V případech, kdy se více instancí stejného atributu používá ve stejném rozsahu, můžete použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> umístit všechny instance atributu do pole. Například, pokud dvě instance `DeveloperAttribute` jsou použity na úrovni třídy stejné třídy, `GetAttribute` metoda můžete upravit tak, aby zobrazení informací v oba atributy nalezen. Nezapomeňte, chcete-li použít více atributů na stejné úrovni, musí být definován atribut s **AllowMultiple** vlastnost nastavena na hodnotu **true** v <xref:System.AttributeUsageAttribute>.  
  
 Následující příklad kódu ukazuje, jak používat **GetCustomAttributes** metodu pro vytvoření pole, které odkazuje na všechny instance `DeveloperAttribute` v žádném zadána třída. Hodnoty všechny atributy se zobrazí konzole.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Pokud nejsou nalezeny žádné atributy, tento kód upozorní uživatele. Jinak, informace obsažené v obou instancí `DeveloperAttribute` se zobrazí.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Načítání více instancí atributu použitého pro různé obory  
 <xref:System.Attribute.GetCustomAttributes%2A> a <xref:System.Attribute.GetCustomAttribute%2A> metody celou třídu a nevrací všechny instance atributu v této třídě. Hledání místo toho najednou pouze jednu zadanou metodu nebo člen. Pokud máte s stejný atribut použitým na každého člena třídy a chcete načíst hodnoty v všechny atributy použité u členů, musíte zadat každou metodu nebo člen jednotlivě na **GetCustomAttributes** a  **GetCustomAttribute**.  
  
 Následující příklad kódu třída jako parametr a hledá `DeveloperAttribute` (definované dříve) na úrovni třídy a každé jednotlivé metody této třídy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Pokud žádné instance `DeveloperAttribute` se nacházejí na úrovni metody nebo úrovni třídy `GetAttribute` metoda upozorní uživatele, že nebyly nalezeny žádné atributy a zobrazí název metody nebo třídu, která neobsahuje atribut. Pokud je atribut nalezen, `Name`, `Level`, a `Reviewed` jsou zobrazeny na konzole.  
  
 Můžete použít členů <xref:System.Type> třídy pro získání jednotlivých metod a členů v předané třídě. Tento příklad nejprve dotazuje **typ** objekt, který chcete získat informace o atributu pro úrovni tříd. Dále je použita <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> pro umístění instancí všech metod do pole <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objekty, které chcete načíst informace o atributu pro úroveň metody. Můžete také <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metoda pro vyhledání atributů na úrovni vlastnosti nebo <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pro vyhledání atributů na úrovni konstruktoru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Atributy](../../../docs/standard/attributes/index.md)
