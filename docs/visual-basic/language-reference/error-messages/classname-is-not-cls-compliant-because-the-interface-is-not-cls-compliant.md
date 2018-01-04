---
title: "& č. 39; &lt;classname&gt;& č. 39; není kompatibilní se specifikací CLS, protože rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39; implementuje není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1f0d1e1f54b6b667431ceae2e346a4118c5b1a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>& č. 39; &lt;classname&gt;& č. 39; není kompatibilní se specifikací CLS, protože rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39; implementuje není kompatibilní se specifikací CLS
Třídy nebo rozhraní je označena jako `<CLSCompliant(True)>` , pokud je odvozena z nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.  
  
 Pro třídy nebo rozhraní splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), jeho hierarchie dědičnosti celý musí splňovat předpisy. To znamená, že každý typ, ze kterého se dědí, přímo ani nepřímo, musí být v souladu. Podobně pokud třída implementuje jedno nebo více rozhraní, se musí být kompatibilní s v rámci své hierarchie dědičnosti.  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud budete potřebovat souladu se specifikací CLS, zadejte tento typ v jiné hierarchii nebo implementace schéma dědičnosti.  
  
-   Pokud požadujete, aby tento typ zůstávají ve své aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.  
  
 
