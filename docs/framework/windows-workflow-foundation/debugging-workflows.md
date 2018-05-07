---
title: Ladění pracovních postupů
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: f41a76cd121373924a408361cfc9074574cc12b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-workflows"></a>Ladění pracovních postupů
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] nabízí několik možností pro ladění pracovních postupů běžících z vývojového prostředí. Pracovní postupy můžete ladit v návrháři, v jazyce XAML a v kódu.  
  
## <a name="debugging-in-the-workflow-designer"></a>Ladění v Návrháři pracovních postupů  
 Zarážky lze nastavit u aktivity v Návrháři pracovních postupů zvýraznění aktivity a stisknutím klávesy **F9** nebo pomocí aktivity kontextové nabídky. Spuštění pracovního postupu pak zalomení při spuštění v režimu ladění hostitele pracovního postupu. Na následujícím snímku obrazovky je na zarážce pozastavena spuštění pracovního postupu. Další informace najdete v tématu [ladění pracovních postupů pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Ladění v jazyce XAML  
 Pokud u zarážky v Návrháři má pozastaví pracovní postup, můžete v jazyce XAML ladit pracovního postupu. Chcete-li zobrazit bodu provádění v jazyce XAML, vyberte **zobrazení jazyka XAML** v Návrháři pracovních postupů při spuštění pracovního postupu je pozastavena. Ladění je možné přepnout zpět do návrháře opakovaným otevřením workflow v Návrháři v Průzkumníku řešení. Další informace najdete v tématu [postupy: ladění XAML pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Ladění v kódu  
 Mohou být používány kód zarážky [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] stejným způsobem, že je lze použít v ostatních aplikacích imperativní. Klikněte na levém okraji podokna kód k vytvoření zarážku kód, nebo stiskněte klávesu **F9** umístěte zarážku v umístění kurzoru.  
  
## <a name="attaching-to-a-workflow-process"></a>Připojení k pracovní postup  
 Pracovní postup ladění také podporuje pomocí sady Visual Studio infrastruktury připojit k procesu. To umožňuje vytvořit pracovní postup k ladění pracovní postup spuštěn v prostředí s jiného hostitele například Internetové informační služby (IIS) 7.0.  
  
## <a name="remote-debugging"></a>Vzdálené ladění  
 Vzdálené ladění Windows Workflow Foundation (WF) funguje stejně jako vzdálené ladění pro jiné komponenty sady Visual Studio. Informace o používání vzdálené ladění najdete v tématu [postupy: povolení vzdáleného ladění](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Pokud je pracovní postup aplikace určena x86 architektura a je hostovaná v počítači se systémem 64bitový operační systém, pak vzdálené ladění nebude fungovat, pokud je na vzdáleném počítači nainstalované sady Visual Studio nebo cíle pro aplikace pracovního postupu se změní na **Žádné procesoru**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Rozšíření ladění služby pracovního postupu  
 Ladicí program služby pracovního postupu je teď veřejná a slouží k vytváření vlastních aplikací, jako jsou monitorování, simulace a ladění znovu hostované Designer. Další informace najdete v tématu <xref:System.Activities.Presentation.Debug.DebuggerService> tématu.
