---
title: "& č. 39; &lt;elementname&gt;& č. 39; je zastaralé (upozornění Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords: BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd6580da794255a3324021a284816ef9700beee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>& č. 39; &lt;elementname&gt;& č. 39; je zastaralé (upozornění Visual Basic)
Příkaz pokusí o přístup k programovací element, který byl označen s <xref:System.ObsoleteAttribute> atribut a direktiva považováno za upozornění.  
  
 Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`. Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu. Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.  
  
 Ve výchozím nastavení, tato zpráva je upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False`. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že je odkaz na zdrojový kód pravopis název elementu správně.  
  
## <a name="see-also"></a>Viz také  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
