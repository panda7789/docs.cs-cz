---
title: Nemůže odkazovat na &#39; &lt;název&gt; &#39; protože je členem pole zadali hodnotu &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;jehož &#39;System.MarshalByRefObject&#39; jako základní třída
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nemůže odkazovat na &#39; &lt;název&gt; &#39; protože je členem pole zadali hodnotu &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;jehož &#39;System.MarshalByRefObject&#39; jako základní třída
`System.MarshalByRefObject` – Třída umožňuje aplikacím, které podporují vzdáleného přístupu k objektům napříč hranicemi domény aplikace. Typy musí dědit z `MarshalByRejectObject` třídy, pokud typ se používá napříč hranicemi domény aplikace. Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, v jakém byly vytvořeny.  
  
 **ID chyby:** BC30310  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte odkaz na zkontrolujte, zda člen odkazovaného je platný.  
  
2.  Explicitně kvalifikaci člena s `Me` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.MarshalByRefObject>  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
