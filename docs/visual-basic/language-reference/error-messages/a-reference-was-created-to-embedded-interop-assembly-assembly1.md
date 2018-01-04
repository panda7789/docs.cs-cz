---
title: "Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce & č. 39; &lt;assembly1&gt;& č. 39; z důvodu nepřímý odkaz na sestavení z sestavení & č. 39;&lt; assembly2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aaaa7460ade00ad4232807ce11ee125e270742bf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce & č. 39; &lt;assembly1&gt;& č. 39; z důvodu nepřímý odkaz na sestavení z sestavení & č. 39;&lt; assembly2&gt;& č. 39;
Odkaz byl vytvořen pro vložené sestavení vzájemné spolupráce se\<assembly1 > se z důvodu nepřímý odkaz na sestavení ze sestavení '\<assembly2 >'. Zvažte změnu vlastnost vložit zprostředkovatel komunikace s objekty typy v jednom ze sestavení.  
  
 Přidáte odkaz na sestavení (assembly1), který má `Embed Interop Types` vlastnost nastavena na hodnotu `True`. To dává pokyn kompilátoru pro vložení informací o zprostředkovatele komunikace s objekty typu z tohoto sestavení. Kompilátor však nemůže vložit spolupráce typ informace z tohoto sestavení, protože jiné sestavení, které se vám (assembly2) také odkazuje dané sestavení (assembly1) a má `Embed Interop Types` vlastnost nastavena na hodnotu `False`.  
  
> [!NOTE]
>  Nastavení `Embed Interop Types` vlastnost na odkaz na sestavení pro `True` je ekvivalentní k odkazování na sestavení s použitím `/link` – možnost kompilátoru příkazového řádku.  
  
 **ID chyby:** BC40059  
  
### <a name="to-address-this-warning"></a>Pro vyřešení tohoto upozornění  
  
-   Chcete-li vložit informace zprostředkovatele komunikace s objekty typu u obou sestavení, nastavte `Embed Interop Types` vlastnost na všechny odkazy na assembly1 na `True`.  
  
-   Chcete-li odebrat upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`. V takovém případě zprostředkovatele komunikace s objekty typu informace jsou poskytovány primární spolupracující sestavení (PIA).  
  
## <a name="see-also"></a>Viz také  
 [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
