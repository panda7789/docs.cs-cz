---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 27cefb1ca1f4748f0d074ffdcd47cd6faa29da00
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320275"
---
# <a name="using-the-wcf-development-tools"></a>Používání vývojářských nástrojů WCF
Tato část popisuje vývojové nástroje sady Visual Studio, které vám můžou pomoct při vývoji WCFservice.  
  
 Šablony sady Visual Studio můžete použít jako základ k rychlému vytvoření vlastní služby a pak k ladění a testování služby použít automatické hostování služby WCF a testovacího klienta WCF. Tyto nástroje společně poskytují rychlý a bezproblémové cyklus ladění a testování a brání nutnosti potvrzování modelu hostování v rané fázi.  
 
 > [!NOTE]
 > Počínaje sadou Visual Studio 2017 nejsou ve výchozím nastavení nainstalovány vývojové nástroje WCF. Aby bylo možné používat tyto funkce, je nutné zajistit, aby byla v instalačním programu sady Visual Studio vybrána součást Windows Communication Foundation.
  
## <a name="the-wcf-developer-tools"></a>Vývojářské nástroje WCF  
 [Šablony sady Visual Studio pro WCF](wcf-vs-templates.md)  
  
 Můžete použít předdefinované šablony projektů a položek sady Visual Studio v aplikaci Visual Studio k rychlému vytváření služeb WCF a okolních aplikací.  
  
 [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 Automatické hostování služby WCF (WcfSvcHost. exe) umožňuje spustit ladicí program sady Visual Studio (F5) pro automatické hostování a testování služby, kterou jste nasadili. Potom můžete službu otestovat pomocí testovacího klienta WCF (wcfTestClient. exe) nebo vašeho vlastního klienta a vyhledat a opravit případné chyby.  
  
 [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 Testovací klient služby WCF (WcfTestClient. exe) je nástroj grafického uživatelského rozhraní, který umožňuje zadat parametry libovolných typů, odeslat tento vstup do služby a zobrazit odpověď, kterou služba odesílá zpět. Poskytuje bezproblémové prostředí pro testování služeb při kombinaci s automatickým hostitelem služby WCF.  
  
 [Generování tříd datových typů z XML](generating-data-type-classes-from-xml.md)  
  
 Data XML uložená ve schránce lze vložit do znakové stránky. Třídy definované v datech budou převedeny na typy kódu.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Používání nástrojů bez oprávnění správce  
 Aby uživatelé bez oprávnění správce mohli vyvíjet služby WCF, vytvoří se seznam ACL (Access Control) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio. Seznam řízení přístupu (ACL) je nastavený na (uživatelské rozhraní), které zahrnuje všechny interaktivní uživatele přihlášené k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje odesílat a přijímat data v šablonách WCF nebo WF v jejich výchozí konfiguraci. Také umožňuje uživatelům používat automatické hostování služby WCF (wcfSvcHost. exe) bez udělení oprávnění správce.  
  
 Přístup můžete upravit pomocí nástroje Netsh. exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem správce se zvýšenými oprávněními. Následuje příklad použití nástroje Netsh. exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o nástroji Netsh. exe najdete v tématu [použití nástroje Netsh. exe a přepínačů příkazového řádku](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Viz také:

- [Šablony sady Visual Studio pro WCF](wcf-vs-templates.md)
- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
