---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: b0997254615ca962fd386dea70c67a8edb36c90a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715531"
---
# <a name="using-the-pick-activity"></a>Použití aktivity Pick
Tato ukázka demonstruje použití aktivity <xref:System.Activities.Statements.Pick>.

 Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování ovládacího prvku založeného na událostech. Chová se podobně jako příkaz C# `switch`, který spouští pouze jednu z větví v příkazu `switch`. Na rozdíl od příkazu `switch`, ve kterém je větev spouštěna na základě hodnoty, aktivita <xref:System.Activities.Statements.Pick> spustí větev na základě toho, jak se aktivita dokončí.

 Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období. Aktivita <xref:System.Activities.Statements.Pick> v ukázce má dvě větve, které jsou spuštěny na základě toho, zda uživatel zadá jméno do 5 sekund nebo ne. Pokud uživatel zadá jméno do 5 sekund, spustí se první větev, která obsahuje vlastní aktivitu `ReadLine`; v opačném případě se spustí druhá větev, která obsahuje aktivitu <xref:System.Activities.Statements.Delay>. Po zadání jména uživatele v konzole nástroje se v konzole vytiskne jméno uživatele. Pokud vstup není zadán do 5 sekund, vypršel časový limit operace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.Activities.Statements.Pick> aktivita

## <a name="discussion"></a>Účely
 Ukázka zahrnuje pracovní postup návrháře a kódovaný pracovní postup.

 Pracovní postup návrháře: verze návrháře ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs: obsahuje funkci `Main`, která spustí ukázkový pracovní postup.

- ReadString.cs: vlastní aktivita, která čte Některé vstupy z konzoly.

- Sequence1. XAML: pracovní postup vytvořený pomocí návrháře, který používá vybrat.

 Kódovaný pracovní postup: kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs: obsahuje funkci `Main`, která spustí ukázkový pracovní postup.

- ReadString.cs: vlastní aktivita, která čte Některé vstupy z konzoly.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení vyskladnit. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
