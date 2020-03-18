---
title: Parametry metody - c# odkaz
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713372"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (Referenční dokumentace jazyka C#)

Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány volané metodě hodnotou. Tuto hodnotu lze změnit v metodě, ale změněná hodnota nebude zachována, když ovládací prvek předá zpět do volající procedury. Pomocí klíčového slova parametr u metody můžete toto chování změnit.  
  
 Tato část popisuje klíčová slova, která můžete použít při deklarování parametrů metody:  
  
- [params](./params.md) určuje, že tento parametr může mít proměnný počet argumentů.
  
- [v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je přečten pouze volanou metodou.
  
- [ref](./ref.md) určuje, že tento parametr je předán odkazem a může být přečten nebo zapsán volanou metodou.
  
- [určuje,](./out-parameter-modifier.md) že tento parametr je předán odkazem a je zapsán volanou metodou.
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
