---
title: Aktivita ThrottledParallelForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715911"
---
# <a name="throttled-parallel-foreach"></a>Aktivita ThrottledParallelForEach

Aktivita `ThrottleParallelForEach` je podobná aktivitě <xref:System.Activities.Statements.ParallelForEach%601> s jednou výjimkou, kterou umožňuje nastavit faktor souběžnosti, aby se omezil počet souběžných větví, které se mají spustit. Aktivita `ThrottleParallelForEach` je odvozena z <xref:System.Activities.NativeActivity>, protože potřebuje naplánovat jiné aktivity (podřízené aktivity) a je přístupná pouze prostřednictvím třídy <xref:System.Activities.NativeActivityContext>.

## <a name="projects"></a>Projekty

|**Názevprojektu**|**Popis**|**Hlavní soubory**|
|-|-|-|
|ThrottledParallelForEach|Obsahuje aktivitu `ThrottledParallelForEach` a její Návrhář.|ThrottledParallelForEach.cs<br /><br /> Definice aktivity `ThrottledParallelForEach`.|
|CodeTestClient|Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup s `ThrottledParallelForEach` pomocí imperativního kódu.|Program.cs<br /><br /> Definuje a spustí instanci ukázkového pracovního postupu.|

## <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor ThrottledParallelForEach. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
