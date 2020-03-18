---
title: Obecné typy za běhu – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a53a21d3028e588f5c4d5ce7bf35fad8d3720a08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75702984"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Obecné typy v běhovém prostředí (Průvodce programováním v C#)
Pokud je obecný typ nebo metoda zkompilován do zprostředkujícího jazyka Microsoft (MSIL), obsahuje metadata, která ji identifikují jako typové parametry. Způsob použití rozhraní MSIL pro obecný typ se liší v závislosti na tom, zda je zadaný parametr typu typ hodnoty nebo typ odkazu.  
  
 Při prvním vytvoření obecného typu s typem hodnoty jako parametr, runtime vytvoří specializovaný obecný typ s dodaným parametrem nebo parametry nahrazenými v příslušných umístěních v msil. Specializované obecné typy jsou vytvořeny jednou pro každý jedinečný typ hodnoty, který se používá jako parametr.  
  
 Předpokládejme například, že kód programu deklaroval zásobník, který je vytvořen z celá čísla:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 V tomto okamžiku runtime generuje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídy, která má celé číslo nahrazeno odpovídajícím způsobem pro jeho parametr. Nyní vždy, když váš programový kód používá zásobník celá čísla, runtime <xref:System.Collections.Generic.Stack%601> znovu používá generované specializované třídy. V následujícím příkladu jsou vytvořeny dvě instance zásobníku celá čísla a sdílejí jednu instanci `Stack<int>` kódu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Předpokládejme však, že jiná <xref:System.Collections.Generic.Stack%601> třída s `long` jiným typem hodnoty, jako je například nebo uživatelem definovaná struktura jako jeho parametr je vytvořen v jiném bodě v kódu. V důsledku toho runtime generuje jinou verzi obecného `long` typu a nahrazuje v příslušných umístěních v MSIL. Převody již nejsou nutné, protože každá specializovaná obecná třída nativně obsahuje typ hodnoty.  
  
 Obecné typy pracují poněkud odlišně pro typy odkazů. Při prvním vytvoření obecného typu s libovolným typem odkazu vytvoří runtime specializovaný obecný typ s odkazy na objekty, které jsou nahrazeny parametry v msil. Potom pokaždé, když je vytvořen typ vytvořena s typem odkazu jako jeho parametr, bez ohledu na to, jaký typ je, runtime opakovaně používá dříve vytvořené specializované verze obecného typu. To je možné, protože všechny odkazy mají stejnou velikost.  
  
 Předpokládejme například, že jste `Customer` měli dva `Order` typy odkazů, třídu a `Customer` třídu, a také předpokládejme, že jste vytvořili stoh typů:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 V tomto okamžiku runtime generuje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídy, která ukládá odkazy na objekty, které budou vyplněny později namísto ukládání dat. Předpokládejme, že další řádek kódu vytvoří zásobník jiného typu odkazu s názvem `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Na rozdíl od typů hodnot není <xref:System.Collections.Generic.Stack%601> pro `Order` daný typ vytvořena jiná specializovaná verze třídy. Místo toho je vytvořena instance specializované <xref:System.Collections.Generic.Stack%601> verze třídy `orders` a proměnná je nastavena tak, aby na ni odkazovala. Předpokládejme, že jste pak narazili na řádek `Customer` kódu pro vytvoření zásobníku typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Stejně jako u <xref:System.Collections.Generic.Stack%601> předchozího použití `Order` třídy vytvořené pomocí typu <xref:System.Collections.Generic.Stack%601> je vytvořena jiná instance specializované třídy. Ukazatele, které jsou obsaženy v něm jsou nastaveny odkazovat `Customer` na oblast paměti velikost typu. Vzhledem k tomu, že počet typů odkazů se může v jednotlivých programech značně lišit, implementace obecných typů jazyka C# výrazně snižuje množství kódu snížením počtu specializovaných tříd vytvořených kompilátorem pro obecné třídy typů odkazů.  
  
 Navíc při obecné c# třída je vytvořena instance pomocí typu hodnoty nebo parametr typu odkazu, reflexe může dotaz za běhu a jeho skutečný typ a jeho parametr typu lze zjistit.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné typy](../../../standard/generics/index.md)
