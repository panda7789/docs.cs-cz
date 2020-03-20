---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183084"
---
# <a name="using-the-wcf-development-tools"></a>Používání vývojářských nástrojů WCF
Tato část popisuje vývojové nástroje sady Visual Studio, které vám mohou pomoci při vývoji služby WCFservice.  
  
 Šablony sady Visual Studio můžete použít jako základ pro rychlé vytvoření vlastní služby a potom pomocí automatického hostitele služby WCF a testovacího klienta WCF k ladění a testování vaší služby. Tyto nástroje společně poskytují rychlé a bezproblémové ladění a testovací cyklus a vylučují potřebu zavázat se k hostitelskému modelu v rané fázi.  

 > [!NOTE]
 > Počínaje Visual Studio 2017, wcf vývojové nástroje nejsou nainstalovány ve výchozím nastavení. Chcete-li tyto funkce používat, je nutné zajistit, aby byla v instalačníslužbě sady Visual Studio vybrána součást Windows Communication Foundation.
  
## <a name="the-wcf-developer-tools"></a>Vývojářské nástroje WCF  
 [Šablony sady Visual Studio pro WCF](wcf-vs-templates.md)  
  
 Předdefinované šablony projektu a položek sady Visual Studio v sadě Visual Studio můžete rychle vytvářet služby WCF a okolní aplikace.  
  
 [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 Automatický hostitel služby WCF (WcfSvcHost.exe) umožňuje spustit ladicí program Sady Visual Studio (F5) pro automatické hostování a testování služby, kterou jste implementovali. Potom můžete otestovat službu pomocí WCF Test Client (wcfTestClient.exe) nebo vlastního klienta najít a opravit případné chyby.  
  
 [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test Client (WcfTestClient.exe) je nástroj GUI, který umožňuje zadat parametry libovolných typů, odeslat tento vstup do služby a zobrazit odpověď, kterou služba odešle zpět. Poskytuje bezproblémové testování služeb v kombinaci s automatickým hostitelem služby WCF.  
  
 [Generování tříd datových typů z XML](generating-data-type-classes-from-xml.md)  
  
 Data XML uložená ve schránce lze vložit do znakové stránky. Třídy definované v datech budou převedeny na typy kódů.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Použití nástrojů bez oprávnění správce  
 Chcete-li uživatelům bez oprávnění správce povolit vývoj služeb WCF, je běhemhttp://+:8731/Design_Time_Addressesinstalace sady Visual Studio vytvořen seznam ACL (Seznam řízení přístupu) pro obor názvů . ACL je nastavena na (UI), který zahrnuje všechny interaktivní uživatele přihlášené k počítači. Správci mohou přidávat nebo odebírat uživatele z tohoto seznamu ACL nebo otevírat další porty. Tento přístupový kód umožňuje šablonám WCF nebo WF odesílat a přijímat data ve výchozí konfiguraci. Umožňuje také uživatelům používat automatický hostitel služby WCF (wcfSvcHost.exe) bez udělení oprávnění správce.  
  
 Přístup můžete upravit pomocí nástroje Netsh.exe v systému Windows Vista pod účtem správce se zvýšenými oprávněními. Následuje příklad použití souboru Netsh.exe.  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o nástroji Netsh.exe naleznete [v tématu Použití nástroje Netsh.exe tool a přepínačů příkazového řádku](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).  
  
## <a name="see-also"></a>Viz také

- [Šablony sady Visual Studio pro WCF](wcf-vs-templates.md)
- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
