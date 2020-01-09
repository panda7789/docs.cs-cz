---
title: Parametry metody – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713372"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (Referenční dokumentace jazyka C#)

Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány metodě volané hodnotou. Tuto hodnotu lze v metodě změnit, ale změněná hodnota nebude zachována, pokud řízení projde zpět do volající procedury. Pomocí klíčového slova parametru metody můžete toto chování změnit.  
  
 Tato část popisuje klíčová slova, která můžete použít při deklaraci parametrů metody:  
  
- [parametry](./params.md) určuje, že tento parametr může mít proměnlivý počet argumentů.
  
- [v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je čten pouze volanou metodou.
  
- [ref](./ref.md) určuje, že tento parametr je předán odkazem a lze jej číst nebo zapsat pomocí volané metody.
  
- [out](./out-parameter-modifier.md) určuje, že tento parametr je předán odkazem a je zapsán metodou volané.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
