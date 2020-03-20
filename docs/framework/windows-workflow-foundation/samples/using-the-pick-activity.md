---
title: Použití aktivity Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142612"
---
# <a name="using-the-pick-activity"></a>Použití aktivity Pick
Tato ukázka ukazuje, <xref:System.Activities.Statements.Pick> jak použít aktivitu.

 Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování řízení založené na událostech. Chová se podobně jako příkaz `switch` C#, který provede pouze jednu `switch` z větví v příkazu. Na `switch` rozdíl od příkazu, ve kterém je větev spuštěna na základě hodnoty, aktivita <xref:System.Activities.Statements.Pick> provede větev na základě toho, jak se aktivita dokončí.

 Tato ukázka vyzve uživatele k zadání jejich jména na konzoli v daném časovém období. Aktivita <xref:System.Activities.Statements.Pick> v ukázce má dvě větve, které jsou provedeny na základě toho, zda uživatel zadá v jejich názvu do 5 sekund nebo ne. Pokud uživatel zadá v jejich názvu do 5 sekund, první `ReadLine` větev je spuštěna, která obsahuje vlastní aktivitu; jinak je spuštěna druhá větev, která obsahuje aktivitu. <xref:System.Activities.Statements.Delay> Jakmile je jméno uživatele zadáno do konzole, je na konzoli vytištěno jeho jméno. Pokud vstup není zadán do 5 sekund, operace je časový rozsah.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.Activities.Statements.Pick>Činnosti.

## <a name="discussion"></a>Diskuse
 Ukázka obsahuje pracovní postup návrháře a kódovaný pracovní postup.

 Pracovní postup návrháře Verze ukázky návrháře ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs : `Main` Zahrnuje funkci, která spustí ukázkový pracovní postup.

- ReadString.cs: Vlastní aktivita, která čte některé vstupy z konzoly.

- Sequence1.xaml: Pracovní postup vytvořený pomocí návrháře, který používá vyskladnění.

 Kódovaný pracovní postup Kódovaná verze ukázky ukazuje, jak vytvořit pracovní postup v návrháři. Jsou zahrnuty následující soubory:

- Program.cs : `Main` Zahrnuje funkci, která spustí ukázkový pracovní postup.

- ReadString.cs: Vlastní aktivita, která čte některé vstupy z konzoly.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení Pick.sln.

2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

3. Chcete-li řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
