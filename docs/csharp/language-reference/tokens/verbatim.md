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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608733"
---
# <a name="-c-reference"></a>@ (C# Referenční dokumentace)

`@` Speciální znak slouží jako doslovné identifikátor. Dá se použít následujícími způsoby:

1. Aby se C# klíčová slova mohla používat jako identifikátory. Znak prefixuje prvek kódu, který kompilátor interpretuje jako identifikátor namísto C# klíčového slova. `@` Následující příklad používá `@` znak k definování identifikátoru s názvem `for` `for` , který používá ve smyčce.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Pro indikaci, že řetězcový literál má být interpretován jako doslovné. Znak v této instanci definuje *doslovné řetězcový literál.* `@` Jednoduché řídicí sekvence (například `"\\"` pro zpětné lomítko), šestnáctkové řídicí sekvence ( `"\x0041"` například pro velké písmeno a) a `"\u0041"` řídicí sekvence Unicode (například pro velké písmeno a) jsou interpretovány doslova. Pouze sekvence escape v uvozovkách`""`() není interpretována doslova; vytvoří jednoduchou uvozovku. Kromě toho nejsou v případě doslovnéch [](interpolated.md) znakových sekvencí (`{{` a `}}`) kulaté závorky řetězcové závorky interpretovány doslova; vytvoří jednoduché znaky složené závorky. Následující příklad definuje dvě totožné cesty k souboru, jeden pomocí regulárního řetězcového literálu a druhý pomocí doslovného řetězcového literálu. Toto je jedno z častých použití doslovnéch řetězcových literálů.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad znázorňuje účinek definování regulárního řetězcového literálu a doslovného řetězcového literálu, který obsahuje identické sekvence znaků.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby kompilátor mohl v případě konfliktu pojmenování rozlišovat mezi atributy. Atribut je třída, která je odvozena z <xref:System.Attribute>. Název jeho typu obvykle obsahuje **atribut**přípony, i když kompilátor vynutil tuto konvenci. Atribut pak může být odkazován v kódu buď jeho úplným názvem typu (například `[InfoAttribute]` nebo jeho zkráceným názvem ( `[Info]`například). Konflikt pojmenování nastane, pokud jsou dva zkrácené názvy typů atributů identické a jeden název typu zahrnuje příponu **atributu** , ale druhá ne. Například následující kód se nepodaří zkompilovat, protože kompilátor nemůže určit, zda `Info` je `Example` atribut nebo `InfoAttribute` použit pro třídu. Další informace najdete v tématu [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Speciální znaky v jazyce C#](./index.md)
