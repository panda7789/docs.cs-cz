---
title: Aktivita ThrottledParallelForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2694173e203fae9b620e9594d6d4a494bdedafef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637763"
---
# <a name="throttled-parallel-foreach"></a>Aktivita ThrottledParallelForEach

`ThrottleParallelForEach` Aktivity se podobá <xref:System.Activities.Statements.ParallelForEach%601> činnost s jednou výjimkou, že umožňuje nastavení faktor souběžnost chcete omezit počet souběžných větve ke spuštění. `ThrottleParallelForEach` Aktivity je odvozena z <xref:System.Activities.NativeActivity>, protože je potřeba naplánovat dalších aktivit (podřízené aktivity) a to je k dispozici pouze prostřednictvím <xref:System.Activities.NativeActivityContext> třídy.

## <a name="projects"></a>Projekty

|**ProjectName**|**Popis**|**Hlavní soubory**|
|-|-|-|
|ThrottledParallelForEach|Obsahuje `ThrottledParallelForEach` aktivita a její návrháře.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` Definici aktivity.|
|CodeTestClient|Ukázková aplikace klienta, který konfiguruje a spustí pracovní postup s `ThrottledParallelForEach` pomocí imperativního kódu.|Program.cs<br /><br /> Definuje a spouští instanci ukázkového pracovního postupu.|

## <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor ThrottledParallelForEach.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Abyste mohli spustit řešení, stiskněte klávesu F5.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
