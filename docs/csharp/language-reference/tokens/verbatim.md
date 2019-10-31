---
title: Odkaz na C# @
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 6f9f16b2639cd9ea57ee7a3030deabf4c1decfbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101563"
---
# <a name="-c-reference"></a>@ (C# Referenční dokumentace)

`@` speciální znak slouží jako doslovné identifikátor. Dá se použít následujícími způsoby:

1. Aby se C# klíčová slova mohla používat jako identifikátory. `@` znak předponu prvku kódu, který kompilátor interpretuje jako identifikátor spíše než C# klíčové slovo. Následující příklad používá `@` znak k definování identifikátoru s názvem `for`, který používá ve `for` smyčce.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Pro indikaci, že řetězcový literál má být interpretován jako doslovné. Znak `@` v této instanci definuje *doslovné řetězcový literál*. Jednoduché řídicí sekvence (například `"\\"` pro zpětné lomítko), šestnáctkové řídicí sekvence (například `"\x0041"` pro velké písmeno A) a řídicí sekvence Unicode (například `"\u0041"` pro velké písmeno A) jsou interpretovány doslova. Pouze sekvence escape v uvozovkách (`""`) nejsou interpretovány doslova; Vytvoří jednoduchou uvozovku. Kromě toho nejsou v případě doslovného počtu znakových sekvencí [řetězcové](interpolated.md) závorky (`{{` a `}}`) interpretovány doslova; poskytují jednoduché znaky složených závorek. Následující příklad definuje dvě totožné cesty k souboru, jeden pomocí regulárního řetězcového literálu a druhý pomocí doslovného řetězcového literálu. Toto je jedno z častých použití doslovnéch řetězcových literálů.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad znázorňuje účinek definování regulárního řetězcového literálu a doslovného řetězcového literálu, který obsahuje identické sekvence znaků.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby kompilátor mohl v případě konfliktu pojmenování rozlišovat mezi atributy. Atribut je třída, která je odvozena z <xref:System.Attribute>. Název jeho typu obvykle obsahuje **atribut**přípony, i když kompilátor vynutil tuto konvenci. Atribut pak může být odkazován v kódu buď jeho úplným názvem typu (například `[InfoAttribute]` nebo jeho zkráceným názvem (například `[Info]`). Konflikt pojmenování nastane, pokud jsou dva zkrácené názvy typů atributů identické a jeden název typu zahrnuje příponu **atributu** , ale druhá ne. Například následující kód se nepodaří zkompilovat, protože kompilátor nemůže určit, zda je atribut `Info` nebo `InfoAttribute` použit pro třídu `Example`. Další informace najdete v tématu [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Speciální znaky v jazyce C#](./index.md)
