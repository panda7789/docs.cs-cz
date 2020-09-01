---
description: Parametry metody – reference jazyka C#
title: Parametry metody – reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134403"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (Referenční dokumentace jazyka C#)

Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány metodě volané hodnotou. Tuto hodnotu lze v metodě změnit, ale změněná hodnota nebude zachována, pokud řízení projde zpět do volající procedury. Pomocí klíčového slova parametru metody můžete toto chování změnit.  
  
 Tato část popisuje klíčová slova, která můžete použít při deklaraci parametrů metody:  
  
- [parametry](./params.md) určuje, že tento parametr může mít proměnlivý počet argumentů.
  
- [v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je čten pouze volanou metodou.
  
- [ref](./ref.md) určuje, že tento parametr je předán odkazem a lze jej číst nebo zapsat pomocí volané metody.
  
- [out](./out-parameter-modifier.md) určuje, že tento parametr je předán odkazem a je zapsán metodou volané.
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
