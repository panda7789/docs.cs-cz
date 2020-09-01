---
description: Reference pro @-C#
title: Reference pro @-C#
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138901"
---
# <a name="-c-reference"></a>@ (Referenční dokumentace jazyka C#)

`@`Speciální znak slouží jako doslovné identifikátor. Dá se použít následujícími způsoby:

1. Aby bylo možné použít klíčová slova jazyka C# jako identifikátory. `@`Znak prefixuje prvek kódu, který kompilátor interpretuje jako identifikátor spíše než klíčové slovo jazyka C#. Následující příklad používá `@` znak k definování identifikátoru s názvem `for` , který používá ve `for` smyčce.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Pro indikaci, že řetězcový literál má být interpretován jako doslovné. `@`Znak v této instanci definuje *doslovné řetězcový literál*. Jednoduché řídicí sekvence (například pro `"\\"` zpětné lomítko), šestnáctkové řídicí sekvence (například `"\x0041"` pro velké písmeno a) a řídicí sekvence Unicode (například `"\u0041"` pro velké písmeno a) jsou interpretovány doslova. Pouze řídicí sekvence uvozovky ( `""` ) nejsou interpretovány doslova; vytvoří jeden znak dvojité uvozovky. Kromě toho nejsou v případě doslovnéch znakových sekvencí (a) kulaté závorky [řetězcové](interpolated.md) závorky `{{` `}}` interpretovány doslova; vytvoří jednoduché znaky složené závorky. Následující příklad definuje dvě totožné cesty k souboru, jeden pomocí regulárního řetězcového literálu a druhý pomocí doslovného řetězcového literálu. Toto je jedno z častých použití doslovnéch řetězcových literálů.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad znázorňuje účinek definování regulárního řetězcového literálu a doslovného řetězcového literálu, který obsahuje identické sekvence znaků.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby kompilátor mohl v případě konfliktu pojmenování rozlišovat mezi atributy. Atribut je třída, která je odvozena z <xref:System.Attribute> . Název jeho typu obvykle obsahuje **atribut**přípony, i když kompilátor vynutil tuto konvenci. Atribut pak může být odkazován v kódu buď jeho úplným názvem typu (například `[InfoAttribute]` nebo jeho zkráceným názvem (například `[Info]` ). Konflikt pojmenování nastane, pokud jsou dva zkrácené názvy typů atributů identické a jeden název typu zahrnuje příponu **atributu** , ale druhá ne. Například následující kód se nepodaří zkompilovat, protože kompilátor nemůže určit, zda `Info` `InfoAttribute` je atribut nebo použit pro `Example` třídu. Další informace najdete v tématu [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Speciální znaky jazyka C#](./index.md)
