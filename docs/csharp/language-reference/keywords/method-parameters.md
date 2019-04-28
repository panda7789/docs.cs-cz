---
title: Parametry metody - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 72917d356ed0fce96502faeef68494c7fdcb214f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661207"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (Referenční dokumentace jazyka C#)

Deklarované parametry pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předávány hodnotou volané metody. Tuto hodnotu můžete změnit v metodě, ale změněné hodnoty nebudou uchována, při řízení se předá zpět do volající procedury. Toto chování můžete změnit pomocí klíčové slovo parametru metody.  
  
 Tato část popisuje klíčová slova, které můžete použít při deklarování parametrů metody:  
  
- [params](../../../csharp/language-reference/keywords/params.md) Určuje, že tento parametr může trvat proměnný počet argumentů.
  
- [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Určuje, že tento parametr je předána odkazem, ale je jen pro čtení ve volané metody.
  
- [REF](../../../csharp/language-reference/keywords/ref.md) Určuje, že tento parametr je předána odkazem a mohou lze číst nebo zapisovat ve volané metody.
  
- [navýšení kapacity](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Určuje, že tento parametr je předána odkazem a je zapsaný ve volané metody.
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
