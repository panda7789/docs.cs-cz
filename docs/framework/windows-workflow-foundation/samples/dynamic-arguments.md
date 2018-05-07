---
title: Dynamické argumenty
ms.date: 03/30/2017
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
ms.openlocfilehash: 5c00b9678191e4e88e9e41380d6b10be39684b3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-arguments"></a>Dynamické argumenty
Tento příklad znázorňuje způsob implementace aktivitu, pro které jsou definovány argumenty příjemce aktivity spíše než Autor aktivity. Dělá to pomocí přepsání způsob, jakým modul runtime vytvoří metadata aktivity.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Před provádění sestavení modulu runtime popis aktivity kontrolou veřejné členy typu aktivity a automaticky deklarace argumenty, proměnné, podřízené aktivity a delegáti aktivity v rámci aktivity metadat. Dělá to zajistit správné vytváření pracovního postupu také jako ke správě spuštění relace a doba platnosti pravidla. Obvykle Autor aktivity definuje argumenty aktivity zadáním veřejné členy na typ aktivity, které pocházejí z <xref:System.Activities.Argument>. Pro každého člena veřejné, která je odvozena z <xref:System.Activities.Argument>, modul runtime vytvoří <xref:System.Activities.RuntimeArgument> a sváže s argumentem zadaný uživatelem nastavit u tohoto člena. V některých případech ale příjemce aktivity poskytuje určitou konfiguraci, která určuje sadu argumentů. Autor aktivity přepsání <xref:System.Activities.Activity.CacheMetadata%2A> přizpůsobit způsob aktivity je integrovaná metadata, která obsahuje sadu argumentů přidružený k aktivitě.  
  
 Tento příklad znázorňuje, jak sestavit seznam argumentů dynamicky pro aktivitu, která volá metodu. Příjemce aktivity Určuje typ a název metody, které chtějí vyvolání společně s kolekce argumenty, které mají být předány této metodě.  
  
> [!NOTE]
>  Účelem této ukázce je ukazují, jak lze přepsat <xref:System.Activities.CodeActivity.CacheMetadata%2A> a jak používat <xref:System.Activities.RuntimeArgument>. Existuje několik upozornění s ohledem na druhy metody, které můžete vyvolat této aktivity. Například nefunguje s obecnými typy nebo pole parametrů. <xref:System.Activities.Statements.InvokeMethod> Aktivity, který se dodává in.NET Framework zpracovává těchto případech a další.  
  
 `MethodInvoke` Aktivity přepsání <xref:System.Activities.CodeActivity.CacheMetadata%2A> a začne tím, že vytvoříte <xref:System.Activities.RuntimeArgument> pro zpracování žádný výsledek z volání metody. To se váže <xref:System.Activities.RuntimeArgument> na veřejně nastavit <xref:System.Activities.OutArgument> s názvem `Result`. Pokud `MethodInvoke.Result` je `null`, automaticky naplní modul runtime, její <xref:System.Activities.OutArgument> nakonfigurované výrazu default pro daný typ. Tímto způsobem aktivita Autor nikdy zkontrolujte, zda je vlastnosti argumentu `null`.  
  
 Dále <xref:System.Activities.CodeActivity.CacheMetadata%2A> určuje přepsání `MethodInfo` používá pro vyvolání z zadaný uživatelem `MethodName` a `TargetType`. `DetermineMethodInfo` Metoda trvá <xref:System.Activities.CodeActivityMetadata> byl předán parametr <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat tak, aby všechny chyby konfigurace mohou být oznámeny jako chyby ověření. To se provádí volání `metadata.AddValidationError`.  
  
 Jednou `MethodInfo` byl nastaven, ukázky iteruje nad `MethodInfo` parametry. Pro každý parametr vytvoří <xref:System.Activities.RuntimeArgument> a sváže s argumentem odpovídající v kolekci zadaný uživatelem z `Parameters` vlastnost. Nakonec kolekce <xref:System.Activities.RuntimeArgument>s je spojené s aktivitou voláním `metadata.SetArgumentsCollection`.  
  
 Můžete provádět v argumentu řešení pomocí <xref:System.Activities.RuntimeArgument>, jako v případě `resultArgument` nebo argument zadaný uživatelem jako v případě `Parameters` kolekce.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DynamicArguments.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`