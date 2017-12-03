---
title: "Používání vývojářských nástrojů WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9532363adafd492ca35e10e6d20c788ddf5b1d17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-development-tools"></a>Používání vývojářských nástrojů WCF
Tato část popisuje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] nástroje pro vývoj, které vám může pomoci při vývoji vaší [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]služby.  
  
 Můžete použít [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablony jako základ rychle vytvářet vlastní služby, potom použijte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta pro ladění a testování vaší služby. Tyto nástroje společně poskytují rychlé a plynulé ladění a testování cyklu a bránit potřeba potvrdit k hostování modelu včas.  
  
## <a name="the-wcf-developer-tools"></a>Nástroje pro vývojáře WCF  
 [Šablony sady Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Můžete použít předdefinovanou [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablon projektů a položek v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] rychle sestavíte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby a okolního aplikace.  
  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Automaticky hostitel služby (WcfSvcHost.exe) umožňuje spustit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicí program (F5) automaticky hostování a testovat službu byla implementována. Potom můžete otestovat pomocí služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testování klienta (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.  
  
 [Testovacího klienta WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Testovacího klienta (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje vstupní parametry náhodné typy, odeslat tento vstup do služby a zobrazení, které odpovědi služba odesílá zpět. Poskytuje bezproblémové služby testování prostředí při kombinaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby.  
  
 [Generování tříd datových typů z XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Data XML uložené do schránky můžete vložit do kódu stránky. Třídy definované v datech se převede na typy kódu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Pomocí nástrojů bez oprávnění správce  
 Aby mohli uživatelé bez oprávnění správce k vývoji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, ACL (seznam řízení přístupu) se vytvoří pro obor názvů "http://+:8731/Design_Time_Addresses" během instalace [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje WCF nebo WF šablon odesílat a přijímat data ve výchozí konfiguraci. Umožňuje také uživatelům používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby (wcfSvcHost.exe) bez je udělení oprávnění správce.  
  
 Můžete upravit přístup pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce. Následuje příklad použití Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe, najdete v části [jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Viz také  
 [Šablony sady Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testovacího klienta WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
