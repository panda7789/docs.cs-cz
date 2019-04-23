---
title: Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 587b35282c7e78da1fdf4ccf9d08214e5665119c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298601"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídy nemůže zapisovat do souboru protokolu, protože:  
  
-   Velikost souboru protokolu (v bajtech) je větší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost  
  
     – a –  
  
-   Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.  
  
2. Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost umožňující větší protokoly.  
  
3. Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> se zahodit zprávy bez upozornění, pokud v protokolu je příliš velký.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
