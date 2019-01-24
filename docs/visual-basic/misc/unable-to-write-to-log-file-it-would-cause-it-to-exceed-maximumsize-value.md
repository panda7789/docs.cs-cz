---
title: Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 170612dfc294f3d2326ad34216f699cf4af6cdb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554657"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídy nemůže zapisovat do souboru protokolu, protože:  
  
-   Velikost souboru protokolu (v bajtech) je větší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost  
  
     – a –  
  
-   Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.  
  
2.  Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost umožňující větší protokoly.  
  
3.  Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> se zahodit zprávy bez upozornění, pokud v protokolu je příliš velký.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
