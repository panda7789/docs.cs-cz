---
title: Obecné typy v C# programovacím průvodci pro dobu běhu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a53a21d3028e588f5c4d5ce7bf35fad8d3720a08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702984"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Obecné typy v běhovém prostředí (Průvodce programováním v C#)
Při kompilaci obecného typu nebo metody do jazyka MSIL (Microsoft Intermediate Language) obsahuje metadata, která ji identifikují jako parametry typu. Způsob, jakým se používá jazyk MSIL pro obecný typ, se liší v závislosti na tom, zda je zadaný parametr typu hodnotový nebo odkazový typ.  
  
 Je-li obecný typ nejprve vytvořen s typem hodnoty jako parametr, modul runtime vytvoří specializovaný obecný typ se zadaným parametrem nebo parametry nahrazeny v příslušných umístěních v jazyce MSIL. Specializované obecné typy jsou vytvořeny jednou pro každý typ jedinečné hodnoty, který se používá jako parametr.  
  
 Předpokládejme například, že váš programový kód deklaruje zásobník, který je tvořen celými čísly:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 V tomto okamžiku modul runtime vygeneruje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídy, která má pro svůj parametr odpovídajícím způsobem celé číslo. Když nyní kód programu používá zásobník celých čísel, modul runtime znovu použije generovanou specializovanou třídu <xref:System.Collections.Generic.Stack%601>. V následujícím příkladu jsou vytvořeny dvě instance celých čísel a sdílejí jednu instanci kódu `Stack<int>`:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Předpokládejme však, že jiná třída <xref:System.Collections.Generic.Stack%601> s jiným typem hodnoty, jako je například `long` nebo uživatelsky definovaná struktura jako její parametr je vytvořena v jiném bodě kódu. V důsledku toho modul runtime vygeneruje jinou verzi obecného typu a nahradí `long` v příslušných umístěních v jazyce MSIL. Převody již nejsou nezbytné, protože každá specializovaná obecná třída nativně obsahuje typ hodnoty.  
  
 Obecné typy fungují trochu jinak pro typy odkazů. Při prvním sestavení obecného typu s jakýmkoli odkazovým typem vytvoří modul runtime specializovaný obecný typ s odkazy na objekty, které jsou nahrazeny pro parametry v jazyce MSIL. Pak při každém vytvoření instance konstruovaného typu s odkazovým typem jako jeho parametr bez ohledu na to, jaký typ je, modul runtime znovu použije dříve vytvořenou specializovanou verzi obecného typu. To je možné, protože všechny odkazy mají stejnou velikost.  
  
 Předpokládejme například, že máte dva typy odkazů, třídu `Customer` a třídu `Order` a předpokládáte také, že jste vytvořili zásobník `Customer`ch typů:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 V tomto okamžiku modul runtime vygeneruje specializovanou verzi třídy <xref:System.Collections.Generic.Stack%601>, která ukládá odkazy na objekty, které budou vyplněny později namísto ukládání dat. Předpokládejme, že další řádek kódu vytvoří zásobník jiného typu odkazu, který je pojmenován `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Na rozdíl od typů hodnot není pro `Order` typ vytvořena jiná specializovaná verze <xref:System.Collections.Generic.Stack%601> třídy. Místo toho je vytvořena instance specializované verze <xref:System.Collections.Generic.Stack%601> třídy a proměnná `orders` je nastavena na odkazování na ni. Předpokládejme, že jste pak narazili na řádek kódu pro vytvoření zásobníku `Customer`ho typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Stejně jako u předchozího použití třídy <xref:System.Collections.Generic.Stack%601> vytvořeného pomocí typu `Order` je vytvořena jiná instance specializované <xref:System.Collections.Generic.Stack%601> třídy. Ukazatele, které jsou obsaženy v nich, jsou nastaveny tak, aby odkazovaly na oblast paměti velikost `Customer`ho typu. Vzhledem k tomu, že se počet typů odkazů může volně odlišovat od programu k programu C# , implementace obecných typů významně snižuje množství kódu snížením počtu specializovaných tříd vytvořených kompilátorem pro obecné třídy typu odkazu.  
  
 Kromě toho, pokud je C# vytvořena instance obecné třídy pomocí typu hodnoty nebo parametru referenčního typu, reflexe se může dotazovat za běhu a jejich skutečný typ a parametr typu se dají zjistit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné typy](../../../standard/generics/index.md)
