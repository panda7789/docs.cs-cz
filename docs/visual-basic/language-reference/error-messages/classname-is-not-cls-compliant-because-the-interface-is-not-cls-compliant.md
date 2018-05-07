---
title: '&#39;&lt;Název třídy&gt; &#39; není kompatibilní se specifikací CLS, protože rozhraní &#39; &lt;interfacename&gt; &#39; se implementuje není kompatibilní se specifikací CLS'
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 4dda0e16a94f43cdb3deeff16fabdd1b10b62526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39;&lt;Název třídy&gt; &#39; není kompatibilní se specifikací CLS, protože rozhraní &#39; &lt;interfacename&gt; &#39; se implementuje není kompatibilní se specifikací CLS
Třídy nebo rozhraní je označena jako `<CLSCompliant(True)>` , pokud je odvozena z nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.  
  
 Pro třídy nebo rozhraní splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), jeho hierarchie dědičnosti celý musí splňovat předpisy. To znamená, že každý typ, ze kterého se dědí, přímo ani nepřímo, musí být v souladu. Podobně pokud třída implementuje jedno nebo více rozhraní, se musí být kompatibilní s v rámci své hierarchie dědičnosti.  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud budete potřebovat souladu se specifikací CLS, zadejte tento typ v jiné hierarchii nebo implementace schéma dědičnosti.  
  
-   Pokud požadujete, aby tento typ zůstávají ve své aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.  
  
 
