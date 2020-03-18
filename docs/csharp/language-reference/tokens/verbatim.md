---
title: '@ - C# Odkaz'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712413"
---
# <a name="-c-reference"></a>@ (Odkaz na C#)

Speciální `@` znak slouží jako doslovný identifikátor. Může být použit následujícími způsoby:

1. Chcete-li povolit c# klíčová slova, která mají být použita jako identifikátory. Znak `@` předponuje element kódu, který kompilátor interpretuje jako identifikátor, nikoli klíčové slovo Jazyka C#. Následující příklad používá `@` znak k definování `for` identifikátoru s `for` názvem, který používá ve smyčce.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Chcete-li označit, že literál řetězce má být interpretován doslovně. Znak `@` v této instanci definuje *doslovný řetězec literál*. Jednoduché sekvence escape (například `"\\"` pro zpětné lomítko), šestnáctkové sekvence `"\x0041"` escape (například pro velké A) a `"\u0041"` sekvence escape Unicode (například pro velké A) jsou interpretovány doslova. Pouze uvozovky`""`escape sekvence ( ) není interpretován doslovně; vytvoří jednu uvozovku. Navíc v případě doslovné [interpolované řetězce](interpolated.md) složená závorka escape sekvence (`{{` a `}}`) nejsou interpretovány doslovně; vytvářejí znaky s jednou závorkou. Následující příklad definuje dvě identické cesty k souborům, jednu pomocí literálu normálního řetězce a druhou pomocí doslovného literálu řetězce. Toto je jeden z více běžných použití doslovných řetězcových literál.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad ilustruje účinek definování normálního řetězcového literálu a doslovného literálu řetězce, které obsahují identické sekvence znaků.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Chcete-li povolit kompilátoru rozlišovat mezi atributy v případech konfliktu názvů. Atribut je třída, která <xref:System.Attribute>je odvozena od . Jeho název typu obvykle zahrnuje atribut přípony **,** i když kompilátor nevynucuje tuto konvenci. Atribut pak může být odkazován v kódu buď jeho `[InfoAttribute]` úplný název typu (například nebo jeho zkrácený název `[Info]`(například). Konflikt pojmenování však dochází, pokud dva zkrácené názvy typů atributů jsou identické a jeden název typu obsahuje příponu **Attribute,** ale druhý ne. Například následující kód se nezdaří kompilovat, `Info` protože `InfoAttribute` kompilátor `Example` nelze určit, zda je atribut nebo použit a třída. Další informace naleznete v [tématu CS1614.](../compiler-messages/cs1614.md)

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Speciální znaky v jazyce C#](./index.md)
