---
title: Obecné typy v běhovém prostředí – Průvodce programováním v C#
description: Seznamte se s obecnými typy v době běhu. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: 8e072e7aa53177929dda0be931beb85863b6a12e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299224"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Obecné typy v běhovém prostředí (Průvodce programováním v C#)
Při kompilaci obecného typu nebo metody do jazyka MSIL (Microsoft Intermediate Language) obsahuje metadata, která ji identifikují jako parametry typu. Způsob, jakým se používá jazyk MSIL pro obecný typ, se liší v závislosti na tom, zda je zadaný parametr typu hodnotový nebo odkazový typ.  
  
 Je-li obecný typ nejprve vytvořen s typem hodnoty jako parametr, modul runtime vytvoří specializovaný obecný typ se zadaným parametrem nebo parametry nahrazeny v příslušných umístěních v jazyce MSIL. Specializované obecné typy jsou vytvořeny jednou pro každý typ jedinečné hodnoty, který se používá jako parametr.  
  
 Předpokládejme například, že váš programový kód deklaruje zásobník, který je tvořen celými čísly:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 V tomto okamžiku modul runtime vygeneruje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídy, která má pro svůj parametr odpovídajícím způsobem celé číslo. Když nyní kód programu používá zásobník celých čísel, modul runtime znovu použije generovanou specializovanou <xref:System.Collections.Generic.Stack%601> třídu. V následujícím příkladu se vytvoří dvě instance celého čísla zásobníku a sdílejí jednu instanci `Stack<int>` kódu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Předpokládejme však, že další <xref:System.Collections.Generic.Stack%601> Třída s jiným typem hodnoty, jako je například `long` nebo uživatelsky definovaná struktura, jako svůj parametr je vytvořena v jiném bodě kódu. V důsledku toho modul runtime vygeneruje jinou verzi obecného typu a nahradí ho `long` v příslušných umístěních v jazyce MSIL. Převody již nejsou nezbytné, protože každá specializovaná obecná třída nativně obsahuje typ hodnoty.  
  
 Obecné typy fungují trochu jinak pro typy odkazů. Při prvním sestavení obecného typu s jakýmkoli odkazovým typem vytvoří modul runtime specializovaný obecný typ s odkazy na objekty, které jsou nahrazeny pro parametry v jazyce MSIL. Pak při každém vytvoření instance konstruovaného typu s odkazovým typem jako jeho parametr bez ohledu na to, jaký typ je, modul runtime znovu použije dříve vytvořenou specializovanou verzi obecného typu. To je možné, protože všechny odkazy mají stejnou velikost.  
  
 Předpokládejme například, že máte dva typy odkazů, `Customer` třídu a `Order` třídu a také Předpokládejme, že jste vytvořili zásobník `Customer` typů:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 V tomto okamžiku modul runtime vygeneruje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídy, která ukládá odkazy na objekty, které budou vyplněny později namísto ukládání dat. Předpokládejme, že další řádek kódu vytvoří zásobník jiného typu odkazu, který má název `Order` :  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Na rozdíl od typů hodnot <xref:System.Collections.Generic.Stack%601> není pro daný typ vytvořena jiná specializovaná verze třídy `Order` . Místo toho je vytvořena instance specializované verze <xref:System.Collections.Generic.Stack%601> třídy a `orders` proměnná je nastavena na odkaz na ni. Předpokládejme, že jste pak narazili na řádek kódu pro vytvoření zásobníku `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Stejně jako u předchozího použití <xref:System.Collections.Generic.Stack%601> třídy vytvořeného pomocí `Order` typu je vytvořena jiná instance specializované <xref:System.Collections.Generic.Stack%601> třídy. Ukazatele, které jsou obsaženy v, jsou nastaveny tak, aby odkazovaly na oblast paměti velikosti `Customer` typu. Vzhledem k tomu, že se počet typů odkazů může volně odlišovat od programu k programu, implementace obecných hodnot v jazyce C# významně snižuje množství kódu tím, že se omezí na jeden počet specializovaných tříd vytvořených kompilátorem pro obecné třídy typu odkazu.  
  
 Kromě toho, pokud je vytvořena instance obecné třídy jazyka C# pomocí typu hodnoty nebo parametru referenčního typu, reflexe se může dotazovat za běhu a jejich skutečný typ a parametr typu se dá zjistit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné typy](../../../standard/generics/index.md)
