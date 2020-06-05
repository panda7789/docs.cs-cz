---
title: Proměnná '<variablename>' je použita před tím, než jí byla přiřazena hodnota.
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406531"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>Proměnná '\<variablename>' je použita před tím, než jí byla přiřazena hodnota.
Proměnná ' \<variablename> ' se používá předtím, než se jí přiřadí hodnota. Výjimka odkazu s hodnotou null by mohla být v době běhu.  
  
 Aplikace má alespoň jednu možnou cestu prostřednictvím kódu, který čte proměnnou před přiřazením jakékoli hodnoty.  
  
 Pokud proměnné nikdy nebyla přiřazena hodnota, obsahuje výchozí hodnotu pro svůj datový typ. Pro referenční datový typ je tato výchozí hodnota [Nothing](../nothing.md). Čtení referenční proměnné, která má hodnotu, `Nothing` může <xref:System.NullReferenceException> v některých případech způsobit určitou situaci.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42104  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že má proměnná platnou hodnotu, než ovládací prvek projde jakýmkoli příkazem, který ho přečte.  
  
- Jedním ze způsobů, jak zaručit, že proměnná vždy má platnou hodnotu, je ji inicializovat jako součást její deklarace. Viz "inicializace" v [příkazu Dim](../statements/dim-statement.md).  
  
## <a name="see-also"></a>Viz také

- [Dim – příkaz](../statements/dim-statement.md)
- [Deklarace proměnné](../../programming-guide/language-features/variables/variable-declaration.md)
- [Řešení potíží s proměnnými](../../programming-guide/language-features/variables/troubleshooting-variables.md)
