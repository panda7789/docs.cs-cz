---
title: "Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; před byla přiřazena hodnota je používána"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords: BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; před byla přiřazena hodnota je používána
Proměnnou '\<NázevProměnné > se před byla přiřazena hodnota je používána. V době běhu může způsobit výjimka odkazu s hodnotou null.  
  
 Aplikace má alespoň jednu cestu možný prostřednictvím jeho kódu, který čte proměnné předtím, než je k němu přiřazen žádnou hodnotu.  
  
 Pokud proměnnou nikdy byla přiřazena hodnota, obsahuje výchozí hodnotu pro jeho datového typu. Pro odkaz na datový typ, že výchozí hodnota je [nic](../../../visual-basic/language-reference/nothing.md). Čtení referenční proměnné, která má hodnotu `Nothing` může způsobit <xref:System.NullReferenceException> v některých případech.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42104  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logika toku řízení a ujistěte se, že proměnná nemá platnou hodnotu před ovládací prvek předává do jakékoli příkaz, který čte ho.  
  
-   Jedním ze způsobů zaručit, že má proměnná vždy platnou hodnotu je k chybě při inicializaci součástí jeho deklaraci. V části "Inicializace" v [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Řešení potíží s proměnnými](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
