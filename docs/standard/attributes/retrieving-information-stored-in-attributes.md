---
title: Načítání informací uložených v atributech
description: Naučte se načítat informace uložené v atributech, například pro instanci atributu, mnoho instancí pro stejný obor, & mnoho instancí pro různé obory.
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
ms.openlocfilehash: cf147a0ae6833039247c4c0878996973cc3db545
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661858"
---
# <a name="retrieving-information-stored-in-attributes"></a>Načítání informací uložených v atributech
Načítání vlastního atributu je jednoduchý proces. Nejprve deklarujte instanci atributu, který chcete načíst. Pak použijte <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodu pro inicializaci nového atributu na hodnotu atributu, který chcete načíst. Po inicializaci nového atributu jednoduše použijete jeho vlastnosti k získání hodnot.  
  
> [!IMPORTANT]
> Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění. Chcete-li načíst atributy pro kód načtený do kontextu pouze pro reflexi, je nutné použít <xref:System.Reflection.CustomAttributeData> třídu, jak je znázorněno v tématu [How to: Loading Assemblies in a Only pouze reflexe](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Tato část popisuje následující způsoby načtení atributů:  
  
- [Načtení jedné instance atributu](#cpconretrievingsingleinstanceofattribute)  
  
- [Načítání více instancí atributu použitých pro stejný obor](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Načítání více instancí atributu použitých pro různé obory](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Načtení jedné instance atributu  
 V následujícím příkladu `DeveloperAttribute` je (popsané v předchozí části) použito pro `MainApp` třídu na úrovni třídy. `GetAttribute`Metoda používá **GetCustomAttribute** k načtení hodnot uložených v `DeveloperAttribute` na úrovni třídy před jejich zobrazením do konzoly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Tento program zobrazí při spuštění následující text.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Pokud atribut není nalezen, metoda **GetCustomAttribute** inicializuje `MyAttribute` na hodnotu null. Tento příklad zkontroluje `MyAttribute` takovou instanci a upozorní uživatele, pokud není nalezen žádný atribut. Pokud `DeveloperAttribute` se v oboru třídy nenajde, zobrazí se v konzole následující zpráva.  
  
```console  
The attribute was not found.
```  
  
 V tomto příkladu se předpokládá, že definice atributu je v aktuálním oboru názvů. Nezapomeňte importovat obor názvů, ve kterém se definice atributu nachází, pokud není v aktuálním oboru názvů.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Načítání více instancí atributu použitých pro stejný obor  
 V předchozím příkladu třída, která se má zkontrolovat, a konkrétní atribut, který se má najít, se předávají <xref:System.Attribute.GetCustomAttribute%2A> . Tento kód funguje dobře, pokud na úrovni třídy je použita pouze jedna instance atributu. Nicméně pokud je více instancí atributu použito na stejné úrovni třídy, metoda **GetCustomAttribute** nenačte všechny informace. V případech, kdy je v rámci stejného oboru použito více instancí stejného atributu, lze použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> k umístění všech instancí atributu do pole Array. Například pokud `DeveloperAttribute` jsou na úrovni třídy stejné třídy použity dvě instance, `GetAttribute` lze metodu upravit tak, aby zobrazovala informace nalezené v obou atributech. Nezapomeňte, že chcete-li použít více atributů na stejné úrovni, atribut musí být definován s vlastností **AllowMultiple** nastavenou na **hodnotu true** v <xref:System.AttributeUsageAttribute> .  
  
 Následující příklad kódu ukazuje, jak použít metodu **GetCustomAttributes** k vytvoření pole, které odkazuje na všechny instance `DeveloperAttribute` v jakékoli dané třídě. Hodnoty všech atributů se pak zobrazí v konzole nástroje.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Pokud nejsou nalezeny žádné atributy, tento kód upozorní uživatele. V opačném případě se zobrazí informace obsažené v obou instancích `DeveloperAttribute` .  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Načítání více instancí atributu použitých pro různé obory  
 <xref:System.Attribute.GetCustomAttributes%2A>Metody a <xref:System.Attribute.GetCustomAttribute%2A> nehledají celou třídu a vracejí všechny instance atributu v této třídě. Místo toho hledají pouze jednu zadanou metodu nebo člen v jednom okamžiku. Pokud máte třídu se stejným atributem použitým pro každého člena a chcete načíst hodnoty ve všech atributech použitých u těchto členů, je nutné každou metodu nebo člen zadat jednotlivě do **GetCustomAttributes** a **GetCustomAttribute**.  
  
 Následující příklad kódu přebírá třídu jako parametr a hledá `DeveloperAttribute` (dříve definovaný) na úrovni třídy a pro každou jednotlivou metodu této třídy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Pokud nejsou nalezeny žádné instance rozhraní na úrovni `DeveloperAttribute` metody nebo třídy, `GetAttribute` Metoda upozorní uživatele, že nebyly nalezeny žádné atributy, a zobrazí název metody nebo třídy, která atribut neobsahuje. Pokud je nalezen atribut, `Name` `Level` pole, a `Reviewed` se zobrazí v konzole nástroje.  
  
 Pomocí členů <xref:System.Type> třídy lze získat jednotlivé metody a členy v předané třídě. Tento příklad nejprve vyhledá objekt **typu** , aby získal informace o atributu pro úroveň třídy. Dále používá <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> k umístění instancí všech metod do pole <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objektů pro načtení informací o atributu pro úroveň metody. Můžete také použít <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodu pro kontrolu atributů na úrovni vlastnosti nebo pro <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> kontrolu atributů na úrovni konstruktoru.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Atributy](index.md)
