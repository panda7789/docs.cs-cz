---
title: Konstruktory instancí – Průvodce programováním v C#
description: Konstruktory instancí v jazyce C# vytvoří a inicializují všechny proměnné členů instance při použití nového výrazu pro vytvoření objektu třídy.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864199"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)

Konstruktory instancí slouží k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu pro vytvoření objektu [třídy](../../language-reference/keywords/class.md). Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, Definujte statický konstruktor. Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).  
  
 Následující příklad ukazuje konstruktor instance:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Pro přehlednost Tato třída obsahuje veřejná pole. Použití veřejných polí není doporučeným způsobem programování, protože umožňuje libovolné metodě kdekoli v programu neomezený a neověřený přístup k vnitřním pracovním postupům objektu. Datové členy by měly být obecně soukromé a měly by být k dispozici pouze prostřednictvím metod a vlastností třídy.  
  
 Tento konstruktor instance se volá vždycky, když se vytvoří objekt založený na `Coords` třídě. Konstruktor podobný tomuto typu, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*. Je však často užitečné poskytnout další konstruktory. Například můžeme přidat konstruktor do `Coords` třídy, která nám umožní zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 To umožňuje `Coords` vytvářet objekty s výchozími nebo konkrétními počátečními hodnotami, jako jsou:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Pokud třída nemá konstruktor, konstruktor bez parametrů se automaticky vygeneruje a k inicializaci polí objektu se použijí výchozí hodnoty. Například hodnota [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializována na hodnotu 0. Informace o výchozích hodnotách typů naleznete v tématu [výchozí hodnoty typů jazyka C#](../../language-reference/builtin-types/default-values.md). Proto vzhledem k tomu, že `Coords` konstruktor bez parametrů třídy inicializuje všechny datové členy na nulu, lze jej odebrat zcela, aniž by bylo nutné měnit způsob fungování třídy. Kompletní příklad použití více konstruktorů je uveden v příkladu 1 dále v tomto tématu a příklad automaticky generovaného konstruktoru je uveden v příkladu 2.  
  
 Konstruktory instancí lze také použít k volání konstruktorů instancí základních tříd. Konstruktor třídy může vyvolat konstruktor základní třídy prostřednictvím inicializátoru následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 V tomto příkladu `Circle` Třída předává hodnoty reprezentující poloměr a výšku do konstruktoru poskytnutého z, `Shape` který `Circle` je odvozen. Úplný příklad s využitím `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu se dvěma konstruktory třídy, jedna bez argumentů a jedna se dvěma argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu třída nemá `Person` žádné konstruktory. v takovém případě je konstruktor bez parametrů k dispozici automaticky a pole jsou inicializována na výchozí hodnoty.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null` .
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje použití inicializátoru základní třídy. `Circle`Třída je odvozena z obecné třídy `Shape` a `Cylinder` Třída je odvozena z `Circle` třídy. Konstruktor u každé odvozené třídy používá svůj inicializátor základní třídy.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Další příklady vyvolání konstruktorů základní třídy naleznete v tématu [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [Base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [static](../../language-reference/keywords/static.md)
