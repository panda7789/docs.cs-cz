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
ms.openlocfilehash: 4f0f3555ae1ab7e662d5f88ac65739a7c791a964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158074"
---
# <a name="retrieving-information-stored-in-attributes"></a>Načítání informací uložených v atributech
Načítání vlastního atributu je jednoduchý proces. Nejprve deklarujte instanci atributu, který chcete načíst. Potom použijte <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodu k inicializaci nového atributu na hodnotu atributu, který chcete načíst. Jakmile je nový atribut inicializován, jednoduše použijete jeho vlastnosti k získání hodnot.  
  
> [!IMPORTANT]
> Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění. Chcete-li načíst atributy pro kód načtený do <xref:System.Reflection.CustomAttributeData> kontextu pouze reflexe, musíte použít třídu, jak je znázorněno v [postupě: Načíst sestavení do kontextu pouze reflexe](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Tato část popisuje následující způsoby načtení atributů:  
  
- [Načítání jedné instance atributu](#cpconretrievingsingleinstanceofattribute)  
  
- [Načítání více instancí atributu použitého ve stejném oboru](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Načítání více instancí atributu aplikovaného na různé obory](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Načítání jedné instance atributu  
 V následujícím příkladu `DeveloperAttribute` (popsanév předchozí části) se `MainApp` použije na třídu na úrovni třídy. Metoda `GetAttribute` používá **GetCustomAttribute** k načtení `DeveloperAttribute` hodnot uložených na úrovni třídy před jejich zobrazením do konzoly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Tento program zobrazí následující text při spuštění.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Pokud atribut nebyl nalezen, **getCustomAttribute** metoda inicializuje `MyAttribute` na hodnotu null. Tento příklad `MyAttribute` zkontroluje pro takovou instanci a upozorní uživatele, pokud není nalezen žádný atribut. Pokud `DeveloperAttribute` není nalezen v oboru třídy, zobrazí se do konzoly následující zpráva.  
  
```console  
The attribute was not found.
```  
  
 Tento příklad předpokládá, že definice atributu je v aktuálním oboru názvů. Nezapomeňte importovat obor názvů, ve kterém je umístěna definice atributu, pokud není v aktuálním oboru názvů.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Načítání více instancí atributu použitého ve stejném oboru  
 V předchozím příkladu jsou třídy ke kontrole a <xref:System.Attribute.GetCustomAttribute%2A>konkrétní atribut najít předány . Tento kód funguje dobře, pokud je na úrovni třídy použita pouze jedna instance atributu. Pokud je však na stejné úrovni třídy použito více instancí atributu, metoda **GetCustomAttribute** nenačte všechny informace. V případech, kdy je ve stejném oboru použito více instancí stejného atributu, můžete použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> k umístění všech instancí atributu do pole. Například pokud jsou na `DeveloperAttribute` úrovni třídy stejné třídy použity dvě instance, lze metodu `GetAttribute` upravit tak, aby zobrazovala informace nalezené v obou atributech. Nezapomeňte, že chcete-li použít více atributů na stejné úrovni, musí být <xref:System.AttributeUsageAttribute>atribut definován s vlastností **AllowMultiple** nastavenou na **hodnotu true** v .  
  
 Následující příklad kódu ukazuje, jak použít metodu **GetCustomAttributes** k vytvoření `DeveloperAttribute` pole, které odkazuje na všechny instance v dané třídě. Hodnoty všech atributů jsou pak zobrazeny do konzoly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Pokud nejsou nalezeny žádné atributy, tento kód upozorní uživatele. V opačném případě se zobrazí informace `DeveloperAttribute` obsažené v obou instancích.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Načítání více instancí atributu použitého pro různé obory  
 Metody <xref:System.Attribute.GetCustomAttributes%2A> <xref:System.Attribute.GetCustomAttribute%2A> a neprohledávají celou třídu a vracejí všechny instance atributu v této třídě. Místo toho prohledávají pouze jednu zadanou metodu nebo člen najednou. Pokud máte třídu se stejným atributem aplikovaný na každého člena a chcete načíst hodnoty ve všech atributech použitých pro tyto členy, musíte zadat každou metodu nebo člen jednotlivě **GetCustomAttributes** a **GetCustomAttribute**.  
  
 Následující příklad kódu bere třídu jako parametr `DeveloperAttribute` a hledá (definované dříve) na úrovni třídy a na každé jednotlivé metody této třídy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Pokud `DeveloperAttribute` nejsou nalezeny žádné instance na úrovni metody `GetAttribute` nebo třídy, metoda upozorní uživatele, že nebyly nalezeny žádné atributy a zobrazí název metody nebo třídy, která neobsahuje atribut. Pokud je nalezen `Name`atribut, `Level`zobrazí `Reviewed` se konzola a pole a pole.  
  
 Členy <xref:System.Type> třídy můžete použít k získání jednotlivých metod a členů v předané třídě. Tento příklad nejprve dotazuje **Type** objekt získat informace o atributpro úroveň třídy. Dále používá <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> k umístění instance všech metod do <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> pole objektů k načtení informací o atributu pro úroveň metody. Metodu <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> můžete také použít ke kontrole atributů <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> na úrovni vlastnosti nebo ke kontrole atributů na úrovni konstruktoru.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Atributy](../../../docs/standard/attributes/index.md)
