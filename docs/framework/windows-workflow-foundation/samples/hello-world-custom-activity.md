---
title: "Hello World vlastní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b05608ca0704483f4318342a733ce363c0a66fc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="hello-world-custom-activity"></a>Hello World vlastní aktivity
Tento příklad znázorňuje několik klíčových funkcích služby [!INCLUDE[wf](../../../../includes/wf-md.md)], včetně toho, jak vytvořit jednoduché vlastní aktivity. Některé funkce předvedená v této ukázce vytváření vlastních aktivit v C# a pomocí `in` a `out` argumenty (<xref:System.Activities.InArgument> a <xref:System.Activities.OutArgument>).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>Vytvoření pracovního postupu v kódu  
 V této ukázce jsou vytvořeny dva vlastní aktivity pomocí kódu jazyka C#. I vlastní aktivity dědí přímo nebo nepřímo <xref:System.Activities.Activity%601> vrátit jednu hodnotu. Výhodou použití obecné návratovou hodnotu, místo, která dědí z neobecnou <xref:System.Activities.Activity> třídy, je, že některé aktivity (například <xref:System.Activities.Statements.Assign>) mají přístup návratovou hodnotu, pokud se používá jako součást složený aktivity.  
  
 AppendString  
 Tato aktivita se dědí z <xref:System.Activities.Activity%601>a používá <xref:System.Activities.Statements.Assign> aktivity, která zřetězí dva řetězce společně.  
  
 Předřadit řetězec  
 Tato aktivita dědí přímo z <xref:System.Activities.CodeActivity%601>a vytvoří podobné funkce jako `AppendString` aktivity, která používá logiku implementované v kódu místo se skládá z předchozích aktivit.  
  
 Následující soubory jsou zahrnuté v tomto projektu.  
  
 AppendString.cs  
 Vlastní aktivity, která připojí řetězce společně. Přebírá v řetězci a jeho kombinuje literálu textovým řetězcem "uvádí hello, world" formuláře dokončení zprávu jako výstup.  
  
 PrependString.cs  
 Tato aktivita předpony řetězec předdefinované tak, aby vstupní řetězec.  
  
 Sequence1.XAML  
 Pracovní postup, který používá `AppendString` a `PrependString` vlastní aktivity.  
  
 Program.cs  
 Program, který spouští pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení HelloWorld.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
## <a name="see-also"></a>Viz také
