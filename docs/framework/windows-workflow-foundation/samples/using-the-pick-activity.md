---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037871"
---
# <a name="using-the-pick-activity"></a>Použití aktivity Pick
Tento příklad ukazuje, jak použít <xref:System.Activities.Statements.Pick> aktivitu.

 <xref:System.Activities.Statements.Pick> Aktivita poskytuje modelování ovládacího prvku založené na událostech. Chová se podobně jako C# `switch` příkaz, který spouští pouze jednu z větví v `switch` příkazu. Na rozdíl od `switch` příkazu <xref:System.Activities.Statements.Pick> , ve kterém je větev spouštěna na základě hodnoty, aktivita provede větev na základě toho, jak se aktivita dokončí.

 Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období. <xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které se spustí na základě toho, jestli uživatel zadá jméno do 5 sekund nebo ne. Pokud uživatel zadá jméno do 5 sekund, spustí se první větev, která obsahuje vlastní `ReadLine` aktivitu. v opačném případě se spustí druhá větev, která <xref:System.Activities.Statements.Delay> obsahuje aktivitu. Po zadání jména uživatele v konzole nástroje se v konzole vytiskne jméno uživatele. Pokud vstup není zadán do 5 sekund, vypršel časový limit operace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.Activities.Statements.Pick>akce.

## <a name="discussion"></a>Účely
 Ukázka zahrnuje pracovní postup návrháře a kódovaný pracovní postup.

 Pracovní postup návrháře: verze návrháře ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs: `Main` Obsahuje funkci, která spustí ukázkový pracovní postup.

- ReadString.cs: Vlastní aktivita, která čte Některé vstupy z konzoly.

- Sequence1. XAML: Pracovní postup vytvořený pomocí návrháře, který používá výběr.

 Kódovaný pracovní postup: kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs: `Main` Obsahuje funkci, která spustí ukázkový pracovní postup.

- ReadString.cs: Vlastní aktivita, která čte Některé vstupy z konzoly.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení vyskladnit. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
