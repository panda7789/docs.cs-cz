---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004728"
---
# <a name="using-the-pick-activity"></a>Použití aktivity Pick
Tato ukázka předvádí, jak používat <xref:System.Activities.Statements.Pick> aktivity.

 <xref:System.Activities.Statements.Pick> Aktivita poskytuje modelování založené na události ovládacího prvku. Se chová podobně jako C# `switch` příkazu, který se spustí pouze jeden z větve ve `switch` příkazu. Na rozdíl od `switch` příkazu, ve kterém je spuštěn větev na základě na základě hodnot <xref:System.Activities.Statements.Pick> aktivity spustí větev na základě způsobu dokončení aktivity.

 Tato ukázka vyzve uživatele k zadání názvu v konzole v daném časovém období. <xref:System.Activities.Statements.Pick> Aktivita v ukázce má dvě větve, které jsou spouštěny na základě Určuje, zda uživatel zadá v jejich názvu do 5 sekund nebo ne. Pokud uživatel zadá v jejich názvu do 5 sekund, je proveden první větev, která obsahuje vlastní `ReadLine` aktivity; jinak jiné větve je spuštěn, které se nachází <xref:System.Activities.Statements.Delay> aktivity. Jakmile se v konzole je zadali uživatelské jméno, uživatelské jméno je vytištěna v konzole. Pokud vstup není zadán do 5 sekund, vypršení časového limitu operace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.Activities.Statements.Pick> aktivita.

## <a name="discussion"></a>Diskuse
 Ukázka zahrnuje Návrháře pracovního postupu a programové pracovního postupu.

 Návrháře návrháři postupu provádění verzi ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Soubor program.cs: Zahrnuje `Main` funkci, která spustí ukázkového pracovního postupu.

- ReadString.cs: Vlastní aktivita, která čte vstupu z konzoly.

- Sequence1.XAML: Pracovní postup vytvořený pomocí návrháře, který používá vybrat.

 Programové pracovního postupu programové verzi ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Soubor program.cs: Zahrnuje `Main` funkci, která spustí ukázkového pracovního postupu.

- ReadString.cs: Vlastní aktivita, která čte vstupu z konzoly.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor řešení Pick.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Abyste mohli spustit řešení, stiskněte klávesu F5.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`