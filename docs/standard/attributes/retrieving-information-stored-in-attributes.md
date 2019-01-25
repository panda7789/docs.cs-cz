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
ms.openlocfilehash: d921c13765f5d61ce9822df0b4059b2cf93a6f6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744082"
---
# <a name="retrieving-information-stored-in-attributes"></a>Načítání informací uložených v atributech
Načítání vlastního atributu je jednoduchý proces. Nejprve deklarujte instanci atributu, který chcete načíst. Potom použijte <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metody k inicializaci nového atributu hodnotu atributu, který chcete načíst. Po inicializaci nový atribut jednoduše pomocí její vlastnosti k získání hodnoty.  
  
> [!IMPORTANT]
>  Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění. Načíst atributy pro kód načtený do kontextu pouze pro reflexi, je nutné použít <xref:System.Reflection.CustomAttributeData> třídy, jak je znázorněno v [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Tato část popisuje načtení atributů následujícími způsoby:  
  
-   [Načítání jednu instanci atributu](#cpconretrievingsingleinstanceofattribute)  
  
-   [Načítání více instancí atributu použít ve stejném rozsahu](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Načítání více instancí atributu použitého k různým oborům](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Načítání jednu instanci atributu  
 V následujícím příkladu `DeveloperAttribute` (popsané v předchozí části) platí pro `MainApp` třídy na úrovni třídy. `GetAttribute` Používá metoda **GetCustomAttribute** k načtení hodnoty uložené v `DeveloperAttribute` na úrovni třídy před zobrazením do konzoly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Tento program zobrazí tento text při spuštění.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Pokud atribut nebyl nalezen, **GetCustomAttribute** metoda inicializuje `MyAttribute` na hodnotu null. Tento příklad kontroluje `MyAttribute` pro takové situaci a upozorní uživatele, pokud není nalezen žádný atribut. Pokud `DeveloperAttribute` nebyla nalezena v oboru třídy do konzoly se zobrazí následující zpráva.  
  
```  
The attribute was not found.   
```  
  
 Tento příklad předpokládá, že definice atributu je v aktuálním oboru názvů. Mějte na paměti pro import oboru názvů, ve kterém se nachází definice atributu, pokud není v aktuálním oboru názvů.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Načítání více instancí atributu použít ve stejném rozsahu  
 V předchozím příkladu třída ke kontrole a k nalezení konkrétní atribut jsou předány <xref:System.Attribute.GetCustomAttribute%2A>. Tento kód funguje dobře, pokud pouze jedna instance atributu se použije na úrovni třídy. Nicméně, pokud více instancí atributu se použije na stejné úrovni třídy, **GetCustomAttribute** metoda nenačte všechny informace. V případech použití více instancí stejného atributu ve stejném rozsahu, můžete použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> pro umístění všech instancí atributu na pole. Například, pokud dva výskyty `DeveloperAttribute` se použijí na úrovni třídy stejné třídy, `GetAttribute` metodu je možné upravit pro zobrazení informací v oba atributy. Mějte na paměti, chcete-li použít několik atributů na stejné úrovni atribut musí být definované s **AllowMultiple** vlastnost nastavena na hodnotu **true** v <xref:System.AttributeUsageAttribute>.  
  
 Následující příklad kódu ukazuje, jak používat **GetCustomAttributes** metodu pro vytvoření pole, která odkazuje na všechny instance `DeveloperAttribute` v libovolné zadané třídy. Hodnoty všech atributů je následně zobrazen konzole.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Pokud nejsou nalezeny žádné atributy, tento kód zobrazí uživateli výstrahu. V opačném případě informace obsažené v obou instancích `DeveloperAttribute` se zobrazí.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Načítání více instancí atributu použitého k různým oborům  
 <xref:System.Attribute.GetCustomAttributes%2A> a <xref:System.Attribute.GetCustomAttribute%2A> metody celou třídu a nevrací všechny instance atributu v dané třídě. Vyhledat místo toho najednou pouze jednu zadanou metodu nebo člen. Pokud máte na stejný atribut u každého člena třídy a chcete načíst hodnoty v všechny atributy použité na tyto členy, je nutné zadat každou metodu nebo člen jednotlivě **GetCustomAttributes** a  **GetCustomAttribute**.  
  
 Následující příklad kódu používá třídu jako parametr a vyhledá `DeveloperAttribute` (definovaného dříve) na úrovni třídy a v každé jednotlivé metody této třídy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Pokud žádné instance `DeveloperAttribute` jsou k dispozici na úrovni metody nebo třídy, `GetAttribute` metoda upozorní uživatele, že nebyly nalezeny žádné atributy a zobrazí název metody nebo třídy, která neobsahuje atribut. Pokud se najde atribut `Name`, `Level`, a `Reviewed` pole se zobrazí v konzole.  
  
 Můžete použít jako objekty její členové <xref:System.Type> třídy pro získání jednotlivé metody a členy v předaných třídě. V tomto příkladu nejdřív dotazuje **typ** můžete získat informace o atributu pro úroveň třídy. V dalším kroku použije <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> umístit všechny metody instance do pole <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objekty se načíst informace o atributu pro úroveň metody. Můžete také použít <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodu ke kontrole atributů na úrovni vlastnosti nebo <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pro vyhledání atributů na úrovni konstruktoru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Atributy](../../../docs/standard/attributes/index.md)
