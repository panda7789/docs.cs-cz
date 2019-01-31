---
title: Výraz má typ '<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 6d366ec750ea5a4505ae5ea618e27f47406ba959
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274009"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>Výraz má typ "\<typename >' který je omezený typ a nelze použít pro přístup ke členům zděděným z 'Object' nebo 'ValueType'
Výraz je vyhodnocen jako typ, který nemůže být pevně určený modulem common language runtime (CLR), ale zpřístupňuje člen, který vyžaduje přetypování pomocí boxingu.  
  
 *Zabalení* odkazuje na zpracování potřebné pro převod na typ `Object` nebo v některých případech k <xref:System.ValueType>. Modul common language runtime nelze například pole určité typy struktur <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, a <xref:System.TypedReference>.  
  
 Tento výraz pokusí použít typ s omezeným přístupem k volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType>, jako například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A>. Přístup k této metodě, Visual Basic Probíhá pokus o implicitní zabalení převod, který způsobí, že k této chybě.  
  
 **ID chyby:** BC31393  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vyhledejte výraz, který se vyhodnotí zmiňovanou typu.  
  
2.  Vyhledejte část, které se pokusí o volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType>.  
  
3.  Přepište příkaz tak, aby se zabránilo volání metody.  
  
## <a name="see-also"></a>Viz také:
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
