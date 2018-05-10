---
title: Služba základních prostředků
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 62b2b863f38647e81468065fd69fc4933afc5b16
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="basic-resource-service"></a>Služba základních prostředků
Tento příklad ukazuje, jak implementovat pomocí modelu programování REST Windows Communication Foundation (WCF), který zveřejňuje kolekce zákazníků, která podporuje načtení služby založené na protokolu HTTP, přidat, odstranit a nahrazovat operace. Tato ukázka se skládá z 2 komponenty - WCF HTTP služba s vlastním hostováním (Service.cs) a konzolovou aplikaci (program.cs), která vytvoří službu a provádí volání do ní.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Služby WCF poskytuje kolekci zákazníkům způsobem prostředků-zaměřené na konkrétní nebo REST. Stručně řečeno to zahrnuje, má jedinečné identifikátory pro kolekci množství zákazníků a každý zákazníka v kolekci. Služba podporuje odesílání HTTP `GET` v kolekci URI k načtení celou kolekci a HTTP `POST` v kolekci identifikátor URI pro přidání nového zákazníka do kolekce. Také v identifikátoru URI pro jednoho zákazníka, podporuje HTTP `GET` zákazník získat tak podrobné údaje, HTTP `PUT` nahradit podrobnosti zákazníka a HTTP `DELETE` zákazník odebrat z kolekce. Při přidání nového zákazníka do kolekce, služba přiřadí ji jedinečný identifikátor URI a ukládá identifikátor URI jako součást podrobnosti zákazníka. Navíc komunikuje identifikátor URI do klienta pomocí HTTP umístění hlavičky odpovědi.  
  
 Soubor App.config Konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> vlastnost nastavena na hodnotu `true`. V důsledku toho WCF vytvoří automatickou HTML na stránku nápovědy na `http://localhost:8000/Customers/help` , který poskytuje informace o tom, jak vytvořit HTTP požadavků a získání přístupu služby odpověď HTTP – například příklad, jak je podrobnosti o odběrateli reprezentované v XML a JSON.  
  
 Vystavení kolekci zákazníků (a obecně platí, žádný prostředek) tímto způsobem, umožníte klientům komunikovat s ním jednotným způsobem pomocí identifikátory URI a HTTP `GET`, `PUT`, `DELETE` a `POST`. Program.cs ukazuje, jak mohou být klienta vytvořené pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že se jedná pouze jeden způsob pro přístup ke službě WCF REST. Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako <xref:System.ServiceModel.ChannelFactory> a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak používat tyto třídy pro komunikaci se službou WCF.  
  
 Služba s vlastním hostováním a klient se skládá vzorku i v konzolové aplikaci spustit. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro základní Ukázka služby prostředků. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce pro vzorovou proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a vyberte **spustit jako správce** v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu Ctrl + F5 a spusťte konzolovou aplikaci. V okně konzoly se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči. Ukázka běží, zapíše klienta stavu aktuální aktivity.  
  
3.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Viz také  
 [Základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
