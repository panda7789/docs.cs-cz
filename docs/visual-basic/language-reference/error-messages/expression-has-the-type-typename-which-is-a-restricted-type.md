---
title: Výraz má typ &#39; &lt;typename&gt; &#39; což je omezený typ a nejde používat pro přistupující členy zděděné z &#39;objekt&#39; nebo &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: d44b9a29f0848508d8cd814e857d9b01819ce7ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535954"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Výraz má typ &#39; &lt;typename&gt; &#39; což je omezený typ a nejde používat pro přistupující členy zděděné z &#39;objekt&#39; nebo &#39;ValueType&#39;
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
