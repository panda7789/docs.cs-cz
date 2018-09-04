---
title: Dynamické argumenty
ms.date: 03/30/2017
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
ms.openlocfilehash: dcf6b84889f3bd7d043f736336c39634cd5384c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530438"
---
# <a name="dynamic-arguments"></a>Dynamické argumenty
Tento příklad ukazuje, jak implementovat aktivitu, pro které jsou definovány argumenty aktivity uživatelů, nikoli autorem aktivity. Dělá to tak, že přepíšete tak, jak modul runtime vytvoří metadat aktivity.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Před provedením vytvoří modul runtime popis aktivity zkoumání veřejné členy typu aktivity a automaticky metadat aktivity v rámci deklarace argumentů, proměnných, podřízené aktivity a delegátů aktivit. Dělá to zajistit správné konstrukce pracovního postupu stejně jako ke správě relací za běhu a pravidla lifetime. Obvykle Autor aktivity definuje argumenty aktivity vytvořením veřejné členy pro typ aktivity, které jsou odvozeny z <xref:System.Activities.Argument>. Pro každý veřejný člen, který je odvozen z <xref:System.Activities.Argument>, vytvoří modul runtime <xref:System.Activities.RuntimeArgument> a sváže s uživatelem zadaného argumentu, nastavte na tento člen. V některých případech však příjemce aktivita poskytuje určitou konfiguraci, která určuje sadu argumentů. Autor aktivity přepíše <xref:System.Activities.Activity.CacheMetadata%2A> přizpůsobit způsob, jak aktivity je sestavená metadata, která obsahuje sadu argumentů přidružený k aktivitě.  
  
 Tento příklad ukazuje, jak sestavit seznam argumentů dynamicky pro aktivitu, která volá metodu. Příjemce aktivit Určuje typ a název metody, které chtějí vyvolat spolu s kolekci argumentů, které se mají předat této metodě.  
  
> [!NOTE]
>  Účelem této ukázce je ukazují, jak přepsat <xref:System.Activities.CodeActivity.CacheMetadata%2A> a jak používat <xref:System.Activities.RuntimeArgument>. Existuje několik upozornění s ohledem na druhy metod, které můžete volat tuto aktivitu. Například nebude fungovat s obecnými typy nebo pole parametrů. <xref:System.Activities.Statements.InvokeMethod> Aktivita, která se dodává v sestaveních.NET Framework zpracovává tyto případy a další.  
  
 `MethodInvoke` Přepsání aktivity <xref:System.Activities.CodeActivity.CacheMetadata%2A> a začíná tím, že vytvoříte <xref:System.Activities.RuntimeArgument> na zpracování jakékoli výsledky z volání metody. To se váže <xref:System.Activities.RuntimeArgument> na veřejně nastavitelné <xref:System.Activities.OutArgument> s názvem `Result`. Pokud `MethodInvoke.Result` je `null`, modul runtime automaticky naplní ho <xref:System.Activities.OutArgument> nakonfigurovanou výchozí výraz pro daný typ. Toto chování znamená, že autor aktivity nikdy zjistit, jestli je vlastnost argument `null`.  
  
 Dále <xref:System.Activities.CodeActivity.CacheMetadata%2A> určuje přepsání `MethodInfo` používá při vyvolání z zadaný uživatel `MethodName` a `TargetType`. `DetermineMethodInfo` Přijímá metodu <xref:System.Activities.CodeActivityMetadata> byl předán parametr <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat tak, aby se případné chyby v konfiguraci může hlásit chyby ověření. To se provádí voláním `metadata.AddValidationError`.  
  
 Jednou `MethodInfo` byl nastaven, ukázka Iteruje přes `MethodInfo` parametry. Pro každý parametr vytvoří <xref:System.Activities.RuntimeArgument> a provádí vazbu na odpovídající argument v kolekci z uživatelem zadaného `Parameters` vlastnost. Nakonec kolekce <xref:System.Activities.RuntimeArgument>je spojené s aktivitou s voláním `metadata.SetArgumentsCollection`.  
  
 Všimněte si, že argument řešení lze provést pomocí <xref:System.Activities.RuntimeArgument>, jako v případě `resultArgument` nebo uživatelem zadaného argumentu, stejně jako v případě `Parameters` kolekce.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DynamicArguments.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`