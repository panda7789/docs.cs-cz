---
title: "Nelze získat datový proud pro protokol"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Nelze získat datový proud pro protokol
Nelze získat datového proudu, do protokolu. Potenciální názvy souborů na základě \<název > se již používá.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třída nelze vytvořit nový soubor protokolu, protože všechny potenciální názvy souborů protokolu na základě \<název > se již používá.  
  
 Má příliš mnoho souborů protokolu může znamenat, že architektury problému s aplikací. Najdete v dokumentaci k <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídu pro další informace.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> nebo <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> zahrnout razítka data v názvu protokolového souboru.  
  
2.  Archivovat existující protokoly a je odebrat z počítače na Povolit <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
