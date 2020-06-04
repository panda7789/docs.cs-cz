---
title: Člen <membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409397"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>Člen \<membername> nekompatibilní se specifikací CLS není povolen v rozhraní kompatibilním se specifikací CLS.
Vlastnost, procedura nebo událost v rozhraní je označena jako, `<CLSCompliant(True)>` když je samotné rozhraní označeno jako `<CLSCompliant(False)>` nebo není označeno.  
  
 Aby rozhraní splňovalo [jazykovou nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí být všechny jeho členy kompatibilní.  
  
 Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40033  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud požadujete kompatibilitu se specifikací CLS a máte kontrolu nad zdrojovým kódem rozhraní, označte rozhraní jako, `<CLSCompliant(True)>` Pokud jsou všechny jeho členy kompatibilní.  
  
- Pokud požadujete kompatibilitu se specifikací CLS a nemáte kontrolu nad zdrojovým kódem rozhraní nebo pokud nesplňuje předpisy, definujte tohoto člena v jiném rozhraní.  
  
- Pokud vyžadujete, aby tento člen zůstal v rámci aktuálního rozhraní, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo ho označte jako `<CLSCompliant(False)>` .  
  
## <a name="see-also"></a>Viz také

- [Interface – příkaz](../statements/interface-statement.md)
