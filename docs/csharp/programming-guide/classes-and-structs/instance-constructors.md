---
title: Konstruktory instancí – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964740"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)

Konstruktory instancí slouží k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu pro vytvoření objektu [třídy](../../language-reference/keywords/class.md). Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, Definujte statický konstruktor. Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).  
  
 Následující příklad ukazuje konstruktor instance:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Pro přehlednost Tato třída obsahuje veřejná pole. Použití veřejných polí není doporučeným způsobem programování, protože umožňuje libovolné metodě kdekoli v programu neomezený a neověřený přístup k vnitřním pracovním postupům objektu. Datové členy by měly být obecně soukromé a měly by být k dispozici pouze prostřednictvím metod a vlastností třídy.  
  
 Tento konstruktor instance se volá vždycky, když se vytvoří objekt založený na třídě `Coords`. Konstruktor podobný tomuto typu, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*. Je však často užitečné poskytnout další konstruktory. Do třídy `Coords` můžeme například přidat konstruktor, který nám umožňuje zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 To umožňuje `Coords` objekty vytvořit s výchozími nebo konkrétními počátečními hodnotami, jako je:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Pokud třída nemá konstruktor, konstruktor bez parametrů se automaticky vygeneruje a k inicializaci polí objektu se použijí výchozí hodnoty. Například hodnota [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializována na hodnotu 0. Informace o výchozích hodnotách typu naleznete v tématu [výchozí hodnoty C# typů](../../language-reference/builtin-types/default-values.md). Proto vzhledem k tomu, že konstruktor bez parametrů `Coords` inicializuje všechny datové členy na nulu, lze jej odebrat zcela, aniž by bylo nutné měnit způsob fungování třídy. Kompletní příklad použití více konstruktorů je uveden v příkladu 1 dále v tomto tématu a příklad automaticky generovaného konstruktoru je uveden v příkladu 2.  
  
 Konstruktory instancí lze také použít k volání konstruktorů instancí základních tříd. Konstruktor třídy může vyvolat konstruktor základní třídy prostřednictvím inicializátoru následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 V tomto příkladu třída `Circle` předává hodnoty reprezentující poloměr a výšku do konstruktoru poskytnutého `Shape`, ze kterého je odvozen `Circle`. Úplný příklad použití `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu se dvěma konstruktory třídy, jedna bez argumentů a jedna se dvěma argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu třída `Person` nemá žádné konstruktory. v takovém případě je konstruktor bez parametrů automaticky zadán a pole jsou inicializována na jejich výchozí hodnoty.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null`.
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje použití inicializátoru základní třídy. Třída `Circle` je odvozena od obecné `Shape`třídy a třída `Cylinder` je odvozena od třídy `Circle`. Konstruktor u každé odvozené třídy používá svůj inicializátor základní třídy.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Další příklady vyvolání konstruktorů základní třídy naleznete v tématu [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [Base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [static](../../language-reference/keywords/static.md)
