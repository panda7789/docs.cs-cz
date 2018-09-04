---
title: Složení základní aktivity
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: ade8187ca44a8182b55cf0f01e5bfe5a9a747255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518373"
---
# <a name="basic-activity-composition"></a>Složení základní aktivity
Tato ukázka předvádí, jak sestavit vlastní aktivity a poskytované systémem aktivity k vytvoření další vlastní aktivity.  
  
 Pracovního postupu pomocí aktivit zjišťování naplánuje průzkum se seznamem dotazy a potom vypíše přijaté odpovědi.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka používá tři vlastní aktivity. `ReadLine` je jednoduchý <xref:System.Activities.NativeActivity> \<řetězec >, který vytváří <xref:System.Activities.Bookmark> při naplánované a nastaví `Return` <xref:System.Activities.OutArgument%601> na hodnotu, se kterým <xref:System.Activities.Bookmark> obnovení. `Prompt` je <xref:System.Activities.Activity%601> \<řetězec >, která má <xref:System.Activities.InArgument%601>< řetězec\> s názvem `Text` a vrátí uživatele v odpovědi `Result` <xref:System.Activities.OutArgument%601> \<řetězec >. `Prompt` Používá aktivitu <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.WriteLine> aktivity, které se dodávají jako součást rozhraní .NET Framework a také zahrnuje vlastní `ReadLine` aktivity pro získávání vstupu uživatele. Poslední vlastní aktivity se `Survey` aktivity. Jde <xref:System.Activities.Activity>< rozhraní ICollection\<řetězec >>.  Tato aktivita přijímá <xref:System.Activities.InArgument%601>< IEnumerable < string\>> s názvem `Questions` a naplní `Result` si argument s odpovědí. `Survey` Používá aktivitu <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.AddToCollection%601> z rozhraní .NET Framework a používá `Prompt` aktivity klást otázky průzkumu a získání odpovědi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřít **BasicActivityComposition.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`