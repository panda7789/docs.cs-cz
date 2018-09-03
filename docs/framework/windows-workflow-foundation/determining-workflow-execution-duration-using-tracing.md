---
title: Určení doby trvání provádění pracovního postupu pomocí trasování
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: c51fdf4543939fc068092b84e02eeb5f52e77d6d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486278"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>Určení doby trvání provádění pracovního postupu pomocí trasování
Toto téma ukazuje, jak určit čas potřebný pro pracovní postup úspěšně dokončila, v místním prostředí ke spuštění pomocí trasování pracovních postupů.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>Chcete-li určit dobu trvání spuštění aplikace pracovního postupu pomocí trasování pracovních postupů  
  
1.  Otevřít [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Vyberte **souboru**, **nové**, **projektu**.  V části **jazyka C#**, vyberte **pracovního postupu** uzlu.  Vyberte **Konzolová aplikace pracovního postupu** ze seznamu šablon.  Název nového projektu `WorkflowDurationTracing` a klikněte na tlačítko **OK**.  
  
2.  Otevřete Workflow1.xaml.  Přetáhněte <xref:System.Activities.Statements.Delay> aktivity na plochu návrháře. Vlastnost doba trvání aktivity přiřadíte hodnotu 00:00:10 (deset sekund).  
  
3.  Otevřete Prohlížeč událostí kliknutím **Start**, **spustit**a zadat `eventvwr.exe`.  
  
4.  Pokud jste ještě nepovolili trasování pracovních postupů, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace** . Vyberte **zobrazení**, **zobrazit analytické a ladit protokoly**. Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**. Prohlížeč událostí ponechte otevřené, aby trasování můžete zobrazit po spuštění pracovního postupu.  
  
5.  Spuštění pracovního postupu aplikace stisknutím kombinace kláves CTRL + SHIFT + B.  
  
6.  V prohlížeči událostí vyhledejte nejnovější událost s ID 1009 a napište zprávu, podobný následujícímu. Poznamenejte si dobu, po kterou zpráva protokolu byla zaznamenána.  
  
 **Nadřazená aktivita ", DisplayName: '', InstanceId: '' naplánovala podřízenou aktivitu"WorkflowDurationTracking.Workflow1", DisplayName:"Workflow1", InstanceId: '1'.**  
  
7.  Najdete další poslední událost s ID 1001 a napište zprávu, podobný následujícímu.  Odečte předchozí čas zprávy od této zprávy protokolováno hodnoty určit dobu trvání provádění pracovního postupu, která by měla být přibližně 10 sekund.  
  
 **WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' byl dokončen v zavřeném stavu.**  
  
## <a name="see-also"></a>Viz také  
 [Trasování pracovních postupů](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
