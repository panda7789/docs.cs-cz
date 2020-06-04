---
title: "'<eventname>' je událost, a proto ji nelze vyvolat přímo."
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409592"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname>' je událost, a proto ji nelze vyvolat přímo.
' <`eventname`> ' je událost, a proto ji nelze vyvolat přímo. `RaiseEvent`K vyvolání události použijte příkaz.  
  
 Volání procedury určuje událost pro název procedury. Obslužná rutina události je procedura, ale samotná událost je signalizační zařízení, které musí být vyvoláno a zpracováno.  
  
 **ID chyby:** BC32022  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Použijte `RaiseEvent` příkaz k signalizaci události a vyvolat proceduru nebo procedury, které ji zpracovávají.  
  
## <a name="see-also"></a>Viz také

- [RaiseEvent – příkaz](../statements/raiseevent-statement.md)
