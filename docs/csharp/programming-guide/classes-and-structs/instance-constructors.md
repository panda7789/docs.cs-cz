---
title: Konstruktory instancí – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964740"
---
# <a name="instance-constructors-c-programming-guide"></a>Konstruktory instancí (Průvodce programováním v C#)

Instance konstruktory se používají k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu k vytvoření objektu [třídy](../../language-reference/keywords/class.md). Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, definujte statický konstruktor. Další informace naleznete [v tématu Statické konstruktory](./static-constructors.md).  
  
 Následující příklad ukazuje konstruktor instance:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Pro přehlednost tato třída obsahuje veřejná pole. Použití veřejných polí není doporučenou programovací praxí, protože umožňuje libovolnou metodu kdekoli v programu neomezený a neověřený přístup k vnitřnímu fungování objektu. Datové členy by obecně měly být soukromé a měly by být přístupné pouze prostřednictvím metod a vlastností třídy.  
  
 Tento konstruktor instance je volána `Coords` vždy, když je vytvořen objekt založený na třídě. Konstruktor, jako je tento, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*. Je však často užitečné poskytnout další konstruktory. Například můžeme přidat konstruktor do `Coords` třídy, která nám umožňuje zadat počáteční hodnoty pro datové členy:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 To `Coords` umožňuje objekty, které mají být vytvořeny s výchozí nebo konkrétní počáteční hodnoty, například toto:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Pokud třída nemá konstruktor, konstruktor bez parametrů je automaticky generován a výchozí hodnoty se používají k inicializaci polí objektu. Například [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializován na 0. Informace o výchozích hodnotách typu naleznete [v tématu Výchozí hodnoty typů jazyka C#](../../language-reference/builtin-types/default-values.md). Proto protože `Coords` konstruktor bez parametrů třídy inicializuje všechny datové členy na nulu, lze jej odebrat zcela bezzměny způsobu fungování třídy. Úplný příklad pomocí více konstruktorů je k dispozici v příkladu 1 dále v tomto tématu a příklad automaticky generovanékonstruktor je k dispozici v příkladu 2.  
  
 Instance konstruktory lze také volat instance konstruktory základních tříd. Konstruktor třídy můžete vyvolat konstruktor základní třídy prostřednictvím inicializátoru, takto:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 V tomto příkladu `Circle` třída předá hodnoty představující poloměr a `Shape` výšku `Circle` konstruktoru, ze kterého je odvozen. Úplný příklad `Shape` pomocí `Circle` a zobrazí se v tomto tématu jako příklad 3.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje třídu se dvěma konstruktory třídy, jeden bez argumentů a jeden se dvěma argumenty.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Příklad 2  
 V tomto příkladu `Person` třída nemá žádné konstruktory, v takovém případě konstruktor bez parametrů je automaticky k dispozici a pole jsou inicializovány na jejich výchozí hodnoty.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Všimněte si, `age` že `0` výchozí hodnota `name` je `null`a výchozí hodnota je .
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad ukazuje pomocí inicializátoru základní třídy. Třída `Circle` je odvozena z `Shape`obecné třídy a `Cylinder` třída `Circle` je odvozena z třídy. Konstruktor na každé odvozené třídy používá jeho základní třídy inicializátoru.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Další příklady při vyvolání konstruktorů základní třídy naleznete v [tématu virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [base](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [Statické](../../language-reference/keywords/static.md)
