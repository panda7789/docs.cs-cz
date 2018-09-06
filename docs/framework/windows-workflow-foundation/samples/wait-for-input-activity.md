---
title: Aktivita Waitforinput
ms.date: 03/30/2017
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
ms.openlocfilehash: 2e878e8c91c5da12a68da848694ce790896517c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741169"
---
# <a name="wait-for-input-activity"></a>Aktivita Waitforinput
Tento příklad ukazuje, jak vytvořit pojmenovaný záložky v pracovním postupu. Windows Workflow Foundation (WF) neposkytuje aktivity pro vytvoření deklarativní záložku. Proto pokud chcete vytvořit záložku v pracovním postupu, musíte napsat vlastní aktivitu, která ji vytvoří. `WaitForInput` Aktivity definované v této ukázce zajišťuje tuto funkci tak, aby uživatelé můžou vytvářet záložky deklarativně v rámci pracovního postupu.  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
  
|**Název projektu**|**Popis**|**Hlavní soubory**|  
|-|-|-|  
|WaitForInput|Obsahuje `WaitForInput` aktivita a její návrháře|WaitForInput.cs<br /><br /> `WaitForInput` definici aktivity.|  
|||WaitForInputDesigner.xaml<br /><br /> Vlastní návrháři u `WaitForInput` aktivity.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Konvertor typu WPF používá k aktualizaci obecného typu aktivity v návrháři.|  
|WaitForInputTestClient|Ukázková klientská aplikace, která konfiguruje a používá pracovního postupu pomocí několika aktivit WaitForInput pomocí návrháře postupu provádění.|Sequence1.XAML<br /><br /> Sekvenční pracovní postup, který používá `WaitForInput` aktivity.|  
|||Program.cs<br /><br /> Spuštění instance pracovního postupu definované v Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>Aktivita WaitForInput  
 `WaitForInput` Aktivita vytvoří pojmenovaný záložku v pracovním postupu. Záložky čeká na signál a přijímá data jeho nakonfigurovaného typu. Po obnovení záložky je k dispozici prostřednictvím data předaná do pracovního postupu `Result` vlastnost.  
  
 `WaitForInput` Aktivity je odvozen od <xref:System.Activities.NativeActivity> třídy, protože se musí vytvořit záložek, které jsou přístupné prostřednictvím pouze <xref:System.Activities.NativeActivityContext> třídy.  
  
 Aktivita má tři atributy použité pro vazbu návrháře, přidání obecný argument funkce, která je možné aktualizovat a nastavení výchozí obecného typu řetězec. Aktivita má také argumenty uvedené v následující tabulce.  
  
|**Jméno**|**Typ**|**Popis**|  
|-|-|-|  
|TResult|Obecný argument (TResult)|Typ záložky. Toto je typ dat, které mají být předány záložku po obnovení.|  
|BookmarkName|Argument InArgument\<řetězec >|Název záložky.|  
|Výsledek|Argument InArgument\<TResult >|Data se předají aktivitě po obnovení záložky.|  
  
## <a name="waitforinput-activity-designer"></a>Návrhář aktivity WaitForInput  
 `WaitForInput` Návrháře aktivit je implementováno v souboru WaitForInputDesigner.xaml. `WaitForInput` Jeho návrháře a aktivity jsou součástí stejného sestavení. Následující grafické ukazuje `WaitForInput` aktivity v sadě nástrojů v rámci kategorie, která má stejný název jako sestavení.  
  
 ![Snímek obrazovky sady nástrojů WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Následující grafické ukazuje `WaitForInput` návrháře. Vzhledem k tomu, `WaitForInput` aktivita je velmi základní, návrháře umožňuje nastavení všechny argumenty přímo v návrhové ploše.  
  
 ![Návrhář aktivity WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor WaitForInput.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Pokud chcete ukázku spustit bez ladění, stiskněte kombinaci kláves CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`