---
title: Počkejte aktivity pro vstup
ms.date: 03/30/2017
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
ms.openlocfilehash: 750a217699abe8b2eb2eaaa364002137d335a41a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wait-for-input-activity"></a>Počkejte aktivity pro vstup
Tento příklad znázorňuje postup vytvoření pojmenovaného záložky v pracovním postupu. Windows Workflow Foundation (WF) neposkytuje aktivitu pro vytvoření deklarativní záložky. Proto pokud chcete vytvořit záložku v pracovní postup, musíte napsat vlastní aktivity, která ji vytvoří. `WaitForInput` Aktivity definované v této ukázce tuto funkci zajišťuje, aby uživatelé mohou vytvářet záložky deklarativně v pracovním postupu.  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
  
|**Název projektu**|**Popis**|**Hlavní soubory**|  
|-|-|-|  
|WaitForInput|Obsahuje `WaitForInput` aktivita a její návrháře|WaitForInput.cs<br /><br /> `WaitForInput` definici aktivity.|  
|||WaitForInputDesigner.xaml<br /><br /> Vlastní designer pro aplikaci `WaitForInput` aktivity.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Převaděče typů WPF použít k aktualizaci obecného typu aktivity v návrháři.|  
|WaitForInputTestClient|Ukázkovou aplikaci klienta, která slouží ke konfiguraci a spustí pracovní postup pomocí několika aktivit WaitForInput pomocí návrháře pracovních postupů.|Sequence1.XAML<br /><br /> Sekvenční pracovní postup, který používá `WaitForInput` aktivity.|  
|||Program.cs<br /><br /> Je spuštěna instance pracovního postupu definované v Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>WaitForInput aktivity  
 `WaitForInput` Aktivity vytvoří pojmenované záložku v pracovním postupu. Záložka čeká na signál a přijímá data typ nakonfigurované. Po obnovení záložku dat předávaných do pracovního postupu je k dispozici prostřednictvím `Result` vlastnost.  
  
 `WaitForInput` Aktivity je odvozena z <xref:System.Activities.NativeActivity> třídy, protože jej musíte vytvořit záložky, které jsou přístupné prostřednictvím jenom <xref:System.Activities.NativeActivityContext> – třída.  
  
 Aktivita má tři atributy použité k němu pro vazby návrháře, přidání obecné argument funkce, která lze aktualizovat a nastavení výchozí obecného typu řetězec. Aktivita má také argumenty uvedené v následující tabulce.  
  
|**Jméno**|**Typ**|**Popis**|  
|-|-|-|  
|TResult|Obecné argument (TResult)|Typ záložky. Jedná se o typ dat mají být předány záložku při obnovení.|  
|NázevZáložky|InArgument\<řetězec >|Název záložky.|  
|Výsledek|InArgument\<TResult >|Data předaná aktivitě při obnovení záložky.|  
  
## <a name="waitforinput-activity-designer"></a>Návrhář aktivity WaitForInput  
 `WaitForInput` Návrhář aktivity je implementována v souboru WaitForInputDesigner.xaml. `WaitForInput` Aktivita a její designer jsou zahrnuté ve stejném sestavení. Následující grafické ukazuje `WaitForInput` aktivity v sadě nástrojů v kategorii, která má stejný název jako sestavení.  
  
 ![Snímek obrazovky sady nástrojů WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 Následující grafické ukazuje `WaitForInput` designer. Protože, `WaitForInput` aktivita je velmi základní, návrháře umožňuje nastavení její argumenty přímo na plochu návrháře.  
  
 ![Návrhář aktivity WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor WaitForInput.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Ukázka bez ladění, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`