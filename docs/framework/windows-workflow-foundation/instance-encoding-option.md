---
title: "Kódování možnost instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a874f88b787a99af0461ff47c3ae246442af2f19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instance-encoding-option"></a>Kódování možnost instance
**Instance kódování možnost** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda zprostředkovatel trvalost SQL by měl komprimovat informace stavu instance pracovního postupu pomocí algoritmu GZip před uložením informace do databáze trvalost. Povolené hodnoty pro tuto vlastnost jsou: GZip a None. Výchozí hodnota je žádné. Následující seznam popisuje tyto možnosti.  
  
1.  **GZip**. Zprostředkovatel trvalost kóduje informace o stavu pomocí algoritmu GZip před uložením informace o stavu v databázi trvalost.  
  
2.  **Žádný**. Zprostředkovatel trvalost neprovádí kódování informace o stavu před uložením informace do databáze trvalost.  
  
 Kódování instance informace o stavu pracovního postupu pomocí GZip snižuje využití paměti v databázi SQL a také snižuje spotřeba síťových, pokud se databáze nachází v jiném počítači v síti z počítače, na která hostitele služby pracovního postupu spuštěna. Obecné pokyny je nastavit **Instance kódování možnost** vlastnost **žádné** Pokud stav instance pracovního postupu je malá.
