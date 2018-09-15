---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625890"
---
# <a name="operationscope"></a>OperationScope
Tato ukázka předvádí, jak zasílání zpráv aktivity, <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> slouží k vystavení existující vlastní aktivity jako operaci služby pracovního postupu. Tato ukázka obsahuje novou vlastní aktivitu, volá se, `OperationScope`. Je určené k usnadnění vývoje služby pracovního postupu tak, že uživatelé můžou vytvářet obsah svého provozu samostatně jako vlastní aktivity a potom je snadno vystavení jako pomocí operace služby `OperationScope` aktivity. Například vlastní `Add` aktivitu, která má dva `in` argumenty a vrací jednu `out` argument může být vystavena jako `Add` operace na službě pracovního postupu přetažením do `OperationScope`.  
  
 Rozsah funguje tak, že kontrola aktivity k dispozici jako jeho obsah. Některé nevázaných `in` argumenty jsou považovány za vstupy z příchozí zprávy. Všechny `out` argumenty, bez ohledu na to, zda jsou vázány, se předpokládá, že se výstupy v následné odpovědi. Název operace vystavené je převzata z zobrazovaný název `OperationScope` aktivity. Konečným výsledkem bude, že je obalen aktivitu tělo <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> s parametry ze zprávy vázán na argumenty aktivity.  
  
 Tato ukázka poskytuje služby pracovního postupu pomocí koncových bodů HTTP. Pokud chcete spustit, je nutné přidat správné seznamy ACL adresy URL. Další informace najdete v tématu [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Spuštěním následujícího příkazu v příkazovém řádku se zvýšenými oprávněními přidá příslušné seznamy ACL (ujistěte se, že uživatelské jméno a doména jsou substituovány za % domény\\% UserName %).  
  
 **netsh http přidat adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení OperationScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Nastavení více projektů spuštění tak, že kliknete pravým tlačítkem na řešení v Průzkumníku řešení a vyberete **nastavit projekty po spuštění**. Přidáte jako více spuštění projektů scénář a Scenario_Client (v uvedeném pořadí).  
  
3.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
    > [!WARNING]
    >  Tento krok je nutný k zobrazení z důvodu vlastní aktivity pracovního postupu BankService.xaml `OperationScope`.  
  
4.  Stisknutím kláves CTRL + F5 spusťte aplikaci. Konzole Scenario_Client vás vyzve k zadání vstupů a odpovídající výstupu se zobrazí v konzole scénář.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`