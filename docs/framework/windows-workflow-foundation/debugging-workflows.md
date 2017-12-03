---
title: "Ladění pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 857f227d8541687768f470633e5430aee2171ea8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="debugging-workflows"></a>Ladění pracovních postupů
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]nabízí několik možností pro ladění pracovních postupů běžících z vývojového prostředí. Pracovní postupy můžete ladit v návrháři, v jazyce XAML a v kódu.  
  
## <a name="debugging-in-the-workflow-designer"></a>Ladění v Návrháři pracovních postupů  
 Zarážky lze nastavit u aktivity v Návrháři pracovních postupů zvýraznění aktivity a stisknutím klávesy **F9** nebo pomocí aktivity kontextové nabídky. Spuštění pracovního postupu pak zalomení při spuštění v režimu ladění hostitele pracovního postupu. Na následujícím snímku obrazovky je na zarážce pozastavena spuštění pracovního postupu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Ladění pracovních postupů pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Ladění v jazyce XAML  
 Pokud u zarážky v Návrháři má pozastaví pracovní postup, můžete v jazyce XAML ladit pracovního postupu. Chcete-li zobrazit bodu provádění v jazyce XAML, vyberte **zobrazení jazyka XAML** v Návrháři pracovních postupů při spuštění pracovního postupu je pozastavena. Ladění je možné přepnout zpět do návrháře opakovaným otevřením workflow v Návrháři v Průzkumníku řešení. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Postupy: ladění kódu XAML pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Ladění v kódu  
 Mohou být používány kód zarážky [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] stejným způsobem, že je lze použít v ostatních aplikacích imperativní. Klikněte na levém okraji podokna kód k vytvoření zarážku kód, nebo stiskněte klávesu **F9** umístěte zarážku v umístění kurzoru.  
  
## <a name="attaching-to-a-workflow-process"></a>Připojení k pracovní postup  
 Pracovní postup ladění také podporuje pomocí sady Visual Studio infrastruktury připojit k procesu. To umožňuje vytvořit pracovní postup k ladění pracovní postup spuštěn v prostředí s jiného hostitele například Internetové informační služby (IIS) 7.0.  
  
## <a name="remote-debugging"></a>Vzdálené ladění  
 [!INCLUDE[wf](../../../includes/wf-md.md)]vzdálené ladění funguje stejně jako vzdálené ladění pro ostatní [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] součásti. Informace o používání vzdálené ladění najdete v tématu [postupy: povolení vzdáleného ladění](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Pokud je pracovní postup aplikace určena x86 architektura a je hostovaná v počítači se systémem 64bitový operační systém, pak vzdálené ladění nebude fungovat, pokud [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] je nainstalován na vzdáleném počítači nebo cíl pro pracovní postup aplikace je změnit. k **žádné procesoru**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Rozšíření ladění služby pracovního postupu  
 Ladicí program služby pracovního postupu je teď veřejná a slouží k vytváření vlastních aplikací, jako jsou monitorování, simulace a ladění znovu hostované Designer. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.Activities.Presentation.Debug.DebuggerService> tématu.
