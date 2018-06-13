---
title: Pomocí aktivity vybrat
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 9617949d72fb1489f66fec205b260b807d011177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516939"
---
# <a name="using-the-pick-activity"></a>Pomocí aktivity vybrat
Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.Pick> aktivity.  
  
 <xref:System.Activities.Statements.Pick> Aktivity poskytuje modelování řízení na základě událostí. Se chová podobně jako jazyka C# `switch` příkaz, který se spustí pouze jeden z poboček v `switch` příkaz. Na rozdíl od `switch` příkaz, ve kterém se spustí větev na základě na hodnotu, <xref:System.Activities.Statements.Pick> aktivita provede větev podle jak dokončení aktivity.  
  
 Tato ukázka vyzve uživatele k zadání v názvu v konzole a v daném časovém intervalu. <xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které jsou spouštěny podle o tom, jestli uživatel zadá v názvu během 5 sekund nebo ne. Pokud uživatel zadá v názvu během 5 sekund, je proveden první větve, který obsahuje vlastní `ReadLine` aktivity; v opačném případě jiné větev proveden, který obsahuje <xref:System.Activities.Statements.Delay> aktivity. Jakmile uživatelské jméno je zadán v v konzole, uživatelské jméno je vytištěno na konzole. Pokud vstup není zadán v rámci 5 sekund, je operace vypršel.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.Pick> aktivita.  
  
## <a name="discussion"></a>Diskusní  
 Ukázka zahrnuje Návrháře pracovního postupu a programové pracovního postupu.  
  
 Návrháře pracovního postupu  
 Návrhář verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:  
  
-   Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.  
  
-   ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.  
  
-   Sequence1.XAML: Pracovní postup vytvořený pomocí návrháře, který používá vyberte.  
  
 Programové pracovního postupu  
 Programové verzi příkladu ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:  
  
-   Program.cs: Zahrnuje `Main` funkce, která spustí ukázkový pracovní postup.  
  
-   ReadString.cs: Vlastní aktivitu, která čte některé vstup z konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Pick.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`