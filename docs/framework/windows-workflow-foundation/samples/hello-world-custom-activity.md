---
title: Vlastní aktivita Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470772"
---
# <a name="hello-world-custom-activity"></a>Vlastní aktivita Hello World
Tento příklad ukazuje několik klíčových funkcí z Windows Workflow Foundation (WF), jak vytvořit jednoduchý vlastní aktivity. Některé funkce v této ukázce jsme vám ukázali vytváříte vlastní aktivity v jazyce C# a pomocí `in` a `out` argumenty (<xref:System.Activities.InArgument> a <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Vytvoření pracovního postupu v kódu  
 V této ukázce jsou dvě vlastní aktivity vytvořené využitím kódu C#. Jak vlastní aktivity dědí přímo nebo nepřímo <xref:System.Activities.Activity%601> vrátit jednu hodnotu. Výhodou použití obecných návratovou hodnotu, namísto dědění z neobecné <xref:System.Activities.Activity> třídy, je, že některé aktivity (například <xref:System.Activities.Statements.Assign>) budou mít přístup k návratovou hodnotu, když se použije jako součást složené aktivity.  
  
 AppendString  
 Tato aktivita se dědí z <xref:System.Activities.Activity%601>a použije <xref:System.Activities.Statements.Assign> aktivitu, která spojuje dva řetězce současně.  
  
 Předřaďte řetězec  
 Tato aktivita dědí přímo z <xref:System.Activities.CodeActivity%601>a vytvoří podobné funkce jako `AppendString` aktivitu, která používá logiku implementovat v kódu namísto se skládá z již existujících aktivit.  
  
 Následující soubory jsou zahrnuty v tomto projektu.  
  
 AppendString.cs  
 Vlastní aktivita, která připojí řetězce dohromady. Přijímá řetězec a zkombinuje je literál textovým řetězcem "říká hello world" do formuláře zprávu o dokončení jako výstup.  
  
 PrependString.cs  
 Tato aktivita předpon předdefinované řetězcové vstupní řetězec.  
  
 Sequence1.XAML  
 Pracovní postup, který se používá `AppendString` a `PrependString` vlastní aktivity.  
  
 Program.cs  
 Program, který spouští pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení HelloWorld.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.