---
title: Člen <membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: 68e1fb4f55d9f9b140f1b54cfde2bc5f60952dd2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592126"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>Non-kompatibilní se Specifikací CLS \<membername > není povolené v rozhraní kompatibilním se Specifikací CLS
Vlastnost, procedura nebo událost v rozhraní je označen jako `<CLSCompliant(True)>` samotným rozhraním, když je označena jako `<CLSCompliant(False)>` nebo není označen.  
  
 V rámci rozhraní má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), všechny její členy musí být kompatibilní.  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40033  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud se vyžadovat dodržování specifikace CLS a máte kontrolu nad rozhraní zdrojového kódu, označte rozhraní jako `<CLSCompliant(True)>` Pokud všechny její členy jsou kompatibilní.  
  
- Pokud vyžadovat dodržování specifikace CLS a nemáte kontrolu nad rozhraní zdrojového kódu, nebo pokud nesplňuje, aby vyhovovala, definujte tohoto člena v rámci jiné rozhraní.  
  
- Pokud budete vyžadovat, že tento člen zůstat v rámci svého aktuálního rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
