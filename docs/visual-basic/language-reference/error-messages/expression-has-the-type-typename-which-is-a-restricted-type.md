---
title: Výraz má typ '<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 0eb30488312cc7519f39a6b819aea15489f2f70a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409517"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>Výraz má typ '\<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.
Výraz je vyhodnocen jako typ, který nemůže být zabalen modulem CLR (Common Language Runtime), ale přistupuje ke členu, který vyžaduje zabalení.  
  
 *Zabalení* odkazuje na zpracování potřebné k převedení typu na `Object` nebo, v některých případech na <xref:System.ValueType> . Modul common language runtime nemůže určit určité typy struktury, například <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> , a <xref:System.TypedReference> .  
  
 Tento výraz se pokusí použít typ s omezením pro volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType> , například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A> . Pro přístup k této metodě Visual Basic došlo k pokusu o implicitní převod zabalení, který tuto chybu způsobuje.  
  
 **ID chyby:** BC31393  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Vyhledejte výraz, který se vyhodnotí na citovaný typ.  
  
2. Vyhledejte část příkazu, která se pokusí zavolat metodu zděděnou z <xref:System.Object> nebo <xref:System.ValueType> .  
  
3. Přepište příkaz, aby se zabránilo volání metody.  
  
## <a name="see-also"></a>Viz také

- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
