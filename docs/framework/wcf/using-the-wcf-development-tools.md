---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 3eb349fd795b2067d4d75ff138fd9b5922110bd3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037874"
---
# <a name="using-the-wcf-development-tools"></a>Používání vývojářských nástrojů WCF
Tato část popisuje nástroje pro vývoj sady Visual Studio, které vám mohou pomoci při vývoji vaší WCFservice.  
  
 Můžete použít šablony sady Visual Studio jako základ pro rychlé vytvoření vlastních služeb a pak pomocí automatického hostitele služby WCF a testovacího klienta WCF pro ladění a testování vaší služby. Tyto nástroje společně poskytují rychlé a bezproblémové ladění a testovací cyklus a bránit potřeba potvrdit na model hostingu v rané fázi.  
  
## <a name="the-wcf-developer-tools"></a>Nástroje pro vývojáře WCF  
 [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Můžete použít předdefinované šablony projektů a položek aplikace Visual Studio v sadě Visual Studio k rychlému vytvoření služby WCF a okolního aplikace.  
  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 Automaticky hostitel služby WCF (WcfSvcHost.exe) umožňuje spustit ladicí program sady Visual Studio (F5) automaticky hostovat a testovat službu, kterou jste implementovali. Potom můžete otestovat pomocí klienta testu WCF (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.  
  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Testovací klient WCF (WcfTestClient.exe) je nástroj grafického uživatelského rozhraní, která umožňuje vstupní parametry libovolných typů, odeslat tento vstup do služby a zobrazení, které odešle zpět odpověď služby. Poskytuje bezproblémové službu testování prostředí v kombinaci s automaticky hostitel služby WCF.  
  
 [Generování tříd datových typů z XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 XML data uložená ve schránce můžete vložit do kódu stránky. Třídy definované v datech se převedou na typy kódu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Pomocí nástroje bez oprávnění správce  
 Pokud chcete povolit uživatelům bez oprávnění správce k vývoji služeb WCF, je vytvořen seznamu ACL portu (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" během instalace sady Visual Studio. Seznam ACL je nastavena na (UI), což zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL povoluje WCF a WF šablon k odesílání a příjmu dat ve své výchozí konfiguraci. Také umožňuje uživatelům používat automaticky hostitel služby WCF (wcfSvcHost.exe) bez nutnosti přidělení oprávnění správce.  
  
 Můžete upravit přístupu pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem se zvýšenými oprávněními správce. Následuje příklad použití Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o Netsh.exe, naleznete v tématu [použití pomocí nástroje Netsh.exe a přepínače příkazového řádku](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Viz také  
 [Šablony sady Visual Studio pro WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
