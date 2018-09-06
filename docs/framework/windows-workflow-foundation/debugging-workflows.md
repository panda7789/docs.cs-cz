---
title: Ladění pracovních postupů
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 17cee1f1b509e777edd3f08c55d473d768b19b55
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861380"
---
# <a name="debugging-workflows"></a>Ladění pracovních postupů
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] nabízí několik možností pro ladění pracovních postupů běžících z vývojového prostředí. Pracovní postupy lze ladit, v návrháři, XAML a kódu.  
  
## <a name="debugging-in-the-workflow-designer"></a>Ladění v Návrháři postupu provádění  
 Zarážky můžete nastavené u aktivit v Návrháři postupu provádění zvýraznění aktivity a stisknutím klávesy **F9** nebo pomocí aktivity kontextové nabídky. Spuštění pracovního postupu pak konce při spuštění hostitele pracovního postupu v režimu ladění. Na následujícím snímku obrazovky je provádění pracovního postupu pozastavení na zarážce. Další informace najdete v tématu [ladění pracovních postupů pomocí návrháře postupu provádění](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Ladění v XAML  
 Pokud pracovní postup má pozastavení na zarážce v návrháři, pracovní postup můžete také ladit v XAML. Chcete-li zobrazit bod provádění v XAML, vyberte **XAML zobrazení** v Návrháři pracovních postupů, když se pozastaví provádění pracovního postupu. Ladění lze přepnout zpátky do návrháře opakovaným otevřením pracovního postupu v Návrháři z Průzkumníka řešení. Další informace najdete v tématu [postupy: ladění XAML pomocí návrháře postupu provádění](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Ladění v kódu  
 Zarážky v kódu lze použít v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] stejným způsobem, že je možné v další naléhavého aplikace. Klikněte na levý okraj podokna kód k vytvoření kódu zarážku, nebo stiskněte klávesu **F9** umístit zarážky na umístění kurzoru.  
  
## <a name="attaching-to-a-workflow-process"></a>Připojení k procesu pracovního postupu  
 Ladění pracovního postupu také podporuje používání infrastruktury sady Visual Studio pro připojení k procesu. To umožňuje Autor pracovního postupu, chcete-li ladit pracovní postup spuštěn v prostředí jiného hostitele, jako je například Internet Information Services (IIS) 7.0.  
  
## <a name="remote-debugging"></a>Vzdálené ladění  
 Vzdálené ladění pro Windows Workflow Foundation (WF) funguje stejně jako vzdálené ladění pro jiné komponenty Visual Studio. Informace o použití vzdáleného ladění, naleznete v tématu [postupy: povolení vzdáleného ladění](https://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Pokud se aplikace pracovního postupu, zaměřuje x86 architektury a je hostovaná na počítači se systémem 64bitový operační systém, vzdálené ladění nebudou fungovat, pokud je na vzdáleném počítači nainstalované sady Visual Studio nebo cíl pro aplikace pracovního postupu se změní na **Jakýkoli procesor**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Rozšíření ladění služby pracovního postupu  
 Služba ladění pracovního postupu je veřejná a slouží k vytváření vlastních aplikací, jako je například monitorování, simulaci a ladění v Návrháři znovu prostředí. Další informace najdete v tématu <xref:System.Activities.Presentation.Debug.DebuggerService> tématu.
