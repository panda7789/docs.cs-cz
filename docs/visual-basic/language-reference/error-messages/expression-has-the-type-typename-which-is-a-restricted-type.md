---
title: Výraz má typ &#39; &lt;typename&gt; &#39; který je typu s omezeným přístupem a nelze použít pro přístup ke členům zděděno z &#39;objekt&#39; nebo &#39;typ hodnoty&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 2ba2298da77ac31abc0b1b4ad84328be7bc6dbb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Výraz má typ &#39; &lt;typename&gt; &#39; který je typu s omezeným přístupem a nelze použít pro přístup ke členům zděděno z &#39;objekt&#39; nebo &#39;typ hodnoty&#39;
Výraz vyhodnocen jako typ, který nemůže být modulem common language runtime (CLR) do pole, ale přistupuje k člena, který vyžaduje zabalení.  
  
 *Zabalení* odkazuje na zpracování potřeba převést na typ `Object` nebo v některých případech k <xref:System.ValueType>. Modul CLR nelze například pole určité typy struktura <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, a <xref:System.TypedReference>.  
  
 Tento výraz se pokusí použít typ s omezeným přístupem pro volání metody zděděno z <xref:System.Object> nebo <xref:System.ValueType>, jako například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A>. Pro přístup k této metodě, se pokusilo jazyka Visual Basic konverzi implicitní zabalení, který způsobuje, že k této chybě.  
  
 **ID chyby:** BC31393  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vyhledejte výraz, který se vyhodnocuje citovaný typu.  
  
2.  Vyhledejte část údajů, které se pokusí zavolat metodu zděděno z <xref:System.Object> nebo <xref:System.ValueType>.  
  
3.  Přepište příkaz tak, aby se zabránilo volání metody.  
  
## <a name="see-also"></a>Viz také  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
