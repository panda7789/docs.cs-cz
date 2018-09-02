---
title: Pokročilé zásady
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387886"
---
# <a name="advanced-policy"></a>Pokročilé zásady
Tento příklad rozšiřuje ukázka jednoduché zásady. Kromě bydliště slevy a obchodní pravidla slevu z příkladu jednoduché zásady bylo přidáno několik nových pravidel.  
  
 Je přidáno pravidlo vysoké hodnoty, která poskytuje větší slevy pro objednávky vysoké hodnoty. Se klíči přiřadí hodnotu priority menší než předchozí dvě pravidla tak, aby se přepsat pole Sleva a přednost nad obou bydliště a obchodní pravidla slevy.  
  
 Vypočítat celkový pravidlo se také přidá, která vypočítá celkový počet vychází z úrovně slev. Ukazuje, jak odkazovat na metody definované v aktivity pracovního postupu, jakož i jak používat ostatní akce. Toto pravidlo také ukazuje řetězení chování, protože je vyhodnocen kdykoli změny pole slevy. Kromě toho metoda přidělování se zobrazí s RuleWriteAttribute CalculateTotal metody. To způsobí, že ovlivněné pravidla (ErrorTotalRule), který se má vyhodnotit znovu pokaždé, když se provede metodu.  
  
 Poslední pravidlo přidali je ten, který zjistí chyby (v tomto případě celkem menší než 0.). V tomto případě zastavení spuštění zásad.  
  
 Nakonec `Console.Writeline` volání jsou přidány jako akce pro každé pravidlo, které poskytují větší přehled o tom spuštění pravidel, a současně zobrazit, že je možné pro přístup ke statické metody na odkazované typy. Můžete také použít sledování, získat přehled o pravidla, které jsou spouštěny.  
  
 Pravidla používaná v této ukázce jsou:  
  
 **ResidentialDiscountRule:**  
  
 Pokud OrderValue > 500 a CustomerType = bydliště  
  
 PAK slevy = 5 %  
  
 **BusinessDiscountRule:**  
  
 Pokud OrderValue > 10000 a CustomerType = firmy  
  
 PAK slevy = 10 %  
  
 **HighValueDiscountRule:**  
  
 Pokud OrderValue > 20000  
  
 PAK slevy = 15 %  
  
 **TotalRule:**  
  
 Pokud slevy > 0  
  
 PAK CalculateTotal (OrderValue slevy)  
  
 JINÉHO celkové = OrderValue  
  
 **ErrorTotalRule:**  
  
 Pokud celkový počet \< 0  
  
 PAK chyba = "Aktivuje ErrorTotalRule"; Zastavení  
  
 Vyhodnocení pravidla a spuštění je možné také prohlížet pomocí sledování a trasování.  
  
### <a name="to-build-the-sample"></a>K vytvoření vzorku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně příkazového řádku sady SDK spusťte soubor .exe ve složce AdvancedPolicy\bin\debug (nebo složky \bin AdvancedPolicy pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Jednoduché zásady](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
