---
title: Obecné třídy – Průvodce programováním v C#
description: Seznamte se s obecnými třídami, které se používají v kolekcích, jako jsou propojené seznamy, zatřiďovací tabulky, zásobníky, fronty a stromy.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 308f4328540e1001018942738d931be3d8be53ed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301915"
---
# <a name="generic-classes-c-programming-guide"></a>Obecné třídy (Průvodce programováním v C#)
Obecné třídy zapouzdřují operace, které nejsou specifické pro konkrétní datový typ. Nejběžnější použití pro obecné třídy je kolekce, jako jsou propojené seznamy, zatřiďovací tabulky, zásobníky, fronty, stromy a tak dále. Operace, jako je přidání a odebrání položek z kolekce, jsou prováděny v podstatě stejným způsobem bez ohledu na typ uložených dat.  
  
 Pro většinu scénářů, které vyžadují třídy kolekcí, je doporučeným přístupem použití těch, které jsou k dispozici v knihovně tříd .NET. Další informace o použití těchto tříd naleznete v tématu [Obecné kolekce v rozhraní .NET](../../../standard/generics/collections.md).  
  
 Obvykle vytvoříte obecné třídy pomocí existující konkrétní třídy a změnou typů na parametry typu po jednom, dokud nedosáhnete optimálního vyvážení generalizace a použitelnosti. Při vytváření vlastních obecných tříd jsou důležité důležité informace, které zahrnují následující:  
  
- Typy, které se mají zobecnit do parametrů typu  
  
     Jako pravidlo, čím více typů můžete parametrizovat, tím flexibilnější a opakovaně použitelný kód se stane. Příliš mnoho generalizace však může vytvořit kód, který je obtížné pro ostatní vývojáře ke čtení nebo pochopení.  
  
- Jaká omezení se mají použít pro parametry typu (viz [omezení u parametrů typu](./constraints-on-type-parameters.md)).  
  
     Dobrým pravidlem je použít maximální možné omezení, které vám pořád umožní zpracovat typy, které musíte zpracovat. Například pokud víte, že vaše obecná třída je určena pouze pro použití s odkazovým typem, použijte omezení třídy. Tím zabráníte nezamýšlenému použití vaší třídy s typy hodnot a umožní vám použít `as` operátor na a `T` Vyhledat hodnoty null.  
  
- Určuje, zda se má faktorovat obecné chování pro základní třídy a podtřídy.  
  
     Vzhledem k tomu, že obecné třídy mohou sloužit jako základní třídy, platí stejné požadavky na návrh jako u neobecné třídy. Přečtěte si pravidla o dědění z obecných základních tříd dále v tomto tématu.  
  
- Zda má být implementováno jedno nebo více obecných rozhraní.  
  
     Například pokud navrhujete třídu, která bude použita k vytváření položek v obecných typech kolekce, bude pravděpodobně nutné implementovat rozhraní, například, <xref:System.IComparable%601> kde `T` je typ vaší třídy.  
  
 Příklad jednoduché obecné třídy naleznete v tématu [Úvod do obecných typů](./index.md).  
  
 Pravidla pro parametry typu a omezení mají několik důsledků pro chování obecné třídy, zejména týkající se dědičnosti a přístupnosti členů. Než budete pokračovat, měli byste pochopit určité výrazy. Pro `Node<T>,` klientský kód obecné třídy může odkazovat na třídu buď zadáním argumentu typu, pro vytvoření uzavřeného konstruovaného typu ( `Node<int>` ). Alternativně může ponechat parametr typu neurčeno, například při zadání obecné základní třídy pro vytvoření otevřeného konstruovaného typu ( `Node<T>` ). Obecné třídy mohou dědit od konkrétních, uzavřených nebo otevřených základních tříd:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Neobecná, jinak řečeno, konkrétní třídy mohou dědit z uzavřených konstruovaných tříd, ale nikoli z otevřených konstruovaných tříd nebo z parametrů typu, protože v době spuštění pro kód klienta není žádný způsob, jak zadat argument typu vyžadovaný pro vytvoření instance základní třídy.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Obecné třídy, které dědí z otevřených konstruovaných typů musí zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny třídou dědění, jak je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Obecné třídy, které dědí z otevřených konstruovaných typů musí určovat omezení, která jsou nadmnožinou, nebo implikuje omezení základního typu:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Obecné typy mohou použít vícenásobné parametry typu a omezení, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Otevřené a uzavřené konstruované typy lze použít jako parametry metody:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Pokud Obecná třída implementuje rozhraní, všechny instance této třídy lze přetypovat na toto rozhraní.  
  
 Obecné třídy jsou invariantní. Jinými slovy, pokud vstupní parametr určuje, zobrazí se `List<BaseClass>` Chyba při kompilaci, pokud se pokusíte zadat `List<DerivedClass>` .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v C#](../index.md)
- [Obecné typy](./index.md)
- [Uložení stavu enumerátorů](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [Skládanka dědičnosti, první část](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
