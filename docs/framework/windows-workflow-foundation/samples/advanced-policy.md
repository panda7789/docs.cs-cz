---
title: "Rozšířené zásady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9752b5779f4fbb525488e88f2f11c98de7b4ba8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-policy"></a>Rozšířené zásady
Tato ukázka rozšiřuje ukázka jednoduché zásady. Kromě domácí slevu a obchodní pravidla slevu z příkladu jednoduché zásady bylo přidáno několik nové pravidel.  
  
 Je přidáno pravidlo vysoké hodnoty, který nabízí větší slevu objednávky vysoké hodnoty. Hodnota priority je vydáno menší než předchozí dvě pravidla tak, aby se přepsat pole slevu a zásada přednost přes obě domácí a obchodní pravidla slevu.  
  
 Celkový počet pravidlo calculate je taky přidaná, která vypočítá celkové založená na úrovni slevy. Zobrazuje, jak odkazovat na aktivitu pracovního postupu je definován metodu, jakož i způsob použití jiného akce. Toto pravidlo také ukazuje, řetězení chování vzhledem k tomu, že bude vyhodnocen kdykoli změny pole slevy. Kromě toho metoda zapisujících se zobrazí s RuleWriteAttribute na metodě CalculateTotal. To způsobí, že dopad pravidla (ErrorTotalRule), který se má znovu vyhodnotit vždy, když se provede metodu.  
  
 Poslední přidat pravidlo je ten, který zjistí chyby (v tomto případě celkem menší než 0). Pokud k tomu dojde, je zastavit zpracování zásad.  
  
 Nakonec `Console.Writeline` volání jsou přidány jako akce pro každé pravidlo zajistit další přehled spuštění pravidla, a současně zobrazit, že je možné odkazovat k přístupu ke statické metody na typy. Můžete také použít sledování získáte tak přehled do pravidla, které jsou spouštěny.  
  
 Pravidla používaná v této ukázce jsou:  
  
 **ResidentialDiscountRule:**  
  
 Pokud OrderValue > 500 a CustomerType = domácí  
  
 PAK slevu = 5 %  
  
 **BusinessDiscountRule:**  
  
 Pokud OrderValue > 10000 a CustomerType = firmy  
  
 PAK slevu = 10 %  
  
 **HighValueDiscountRule:**  
  
 Pokud OrderValue > 20000  
  
 PAK slevu = 15 %  
  
 **TotalRule:**  
  
 Pokud slevách > 0  
  
 PAK CalculateTotal (OrderValue, slevy)  
  
 ELSE celkem = OrderValue  
  
 **ErrorTotalRule:**  
  
 Pokud celkový počet \< 0  
  
 POTOM chyba = "Aktivováno ErrorTotalRule"; Zastavení  
  
 Vyhodnocení pravidla a provádění můžete zobrazit také prostřednictvím trasování a sledování.  
  
### <a name="to-build-the-sample"></a>Chcete-li sestavit ukázku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně příkazového řádku sady SDK spusťte soubor .exe ve složce AdvancedPolicy\bin\debug (nebo složky \bin AdvancedPolicy pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Jednoduché zásady](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
