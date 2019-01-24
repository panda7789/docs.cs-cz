---
title: '&#39;&lt;Třída elementname&gt; &#39; je zastaralý (upozornění jazyka Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: eeeca3354592bfc6d657b435c42ad5644fd2b97d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552387"
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>&#39;&lt;Třída elementname&gt; &#39; je zastaralý (upozornění jazyka Visual Basic)
Příkaz se pokusí o přístup k programový element, která byla označena atributem <xref:System.ObsoleteAttribute> atribut a směrnice s ní zacházet jako upozornění.  
  
 Můžete označit libovolný programovací element jako se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost buď `True` nebo `False`. Pokud ji nastavíte na `True`, kompilátor zpracovává pokus o použití prvku za chybu. Pokud ji nastavíte na `False`, nebo jej jako výchozí `False`, kompilátor vyvolá upozornění, pokud se pokus o použití elementu.  
  
 Ve výchozím nastavení, je tato zpráva upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False`. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že odkaz zdrojového kódu je správně kontroly pravopisu název elementu.  
  
## <a name="see-also"></a>Viz také:
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
