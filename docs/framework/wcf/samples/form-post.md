---
title: Zpracování odeslaného formuláře
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31d2ebbdb6f899390d7b3af485c1583fb80ae6dc
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="form-post"></a>Zpracování odeslaného formuláře
Tento příklad znázorňuje postup rozšíření programovací model REST WCF pro nové formáty příchozí žádosti o podporu. Ukázka také zahrnuje implementaci formátovací modul, který může deserializovat požadavek z post formuláře HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Kromě toho příklad používá šablony T4 vrátit stránku HTML, který poskytuje formuláře HTML, který uživatelé vystavit zpět ke službě WCF REST.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Rozšíření podpory pro příchozí požadavek formáty.  
  
-   Integrace šablon T4.  
  
## <a name="discussion"></a>Diskusní  
 Tato ukázka se skládá ze dvou projektů. Jeden projekt je HtmlFormProcessing knihovny, která obsahuje vlastní požadavek formátovací modul, který může deserializovat příspěvcích formuláře HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy. Druhý projekt je konzolová aplikace, která rozšiřuje ukázka základní služby prostředků použít vlastní požadavek formátování HtmlFormProcessing knihovny.  
  
 Vlastní formátovací modul, který může deserializovat příspěvcích formuláře HTML (HtmlFormRequestDispatchFormatter) přijme, i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které lze převést z řetězce pomocí <xref:System.ServiceModel.Dispatcher.QueryStringConverter> a označené jako typy <xref:System.Runtime.Serialization.DataContractAttribute> které mají pouze členové, které mohou být převést z řetězce pomocí QueryStringConverter.  
  
 Tento projekt knihovny HtmlFormProcessing také zahrnuje abstraktní základní třídu, `RequestBodyDispatchFormatter`, který slouží k vytvoření další vlastní požadavek formátování. Odvozování z `RequestBodyDispatchFormatter` umožňuje vývojáři soustředit na deserializace logiku textu požadavku, která umožňuje základní třídu pro mapování parametrů šablony URI pro parametry metody operace. Také v knihovně HtmlFormProcessing je projekt `HtmlFormProcessingBehavior` třídy, která ukazuje, jak jsou odvozeny od <xref:System.ServiceModel.Description.WebHttpBehavior> nahradit výchozí formátování požadavek formátování vlastní požadavek.  
  
 Tento projekt konzolové aplikace rozšiřuje [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázka. Ukázka základní služby prostředků ukazuje, jak vystavit prostředek způsobem, který využívá programovací model REST WCF. V ukázce základní služba prostředků je prostředek kolekce zákazníka zpřístupněná tak, aby zákazníci v kolekci můžete vytvořit, načíst, aktualizovat a odstranit. Ukázka základní služby prostředků používá jenom dva nativně podporované příchozí požadavek formáty, XML a JSON.  
  
 Konzolové aplikace v této ukázce Post formuláře využívá vlastní formátování v knihovně HtmlFormProcessing, což umožňuje uživatelům vytvářet zákazníkům odesláním požadavku z post formuláře HTML pomocí prohlížeče. Také přidá operace, která vrátí stránku HTML, obsahující formulář odeslán zpět ke službě. Tuto stránku HTML, je generována pomocí předběžně zpracované T4 šablonu, která se skládá z soubor .tt a .cs automaticky generovaný soubor. Soubor .tt umožňuje vývojáři k zápisu odpovědi v podobě šablony, který obsahuje proměnné a řízení struktury. Další informace o T4 najdete v tématu [generování artefaktů podle pomocí textových šablon](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku Post formuláře. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce a ukázku úspěšně vykonat. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a výběr "Spustit jako správce" v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu CTRL + F5 a spusťte projekt konzolové aplikace FormPost.  
  
3.  V okně konzoly se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy.  
  
4.  Ukázka běží, klient zapíše stavu aktuální aktivity, jestli ho přidávat zákazníka, aktualizace zákazníka, odstraňování zákazníka nebo získáním seznamu aktuální zákazníků ze služby do okna konzoly.  
  
5.  Zobrazí se výzva a přejděte k identifikátoru URI zákazníka formuláře. Otevřete prohlížeč a přejděte na daný identifikátor URI. Zadejte název a adresu pro odběratele a kliknutím **odeslání** tlačítko.  
  
6.  Stisknutím libovolné klávesy okna konzoly pokračovat v provozu vzorku.  
  
7.  Ukázku dokončení, Všimněte si, že zákazník, kterou jste vytvořili pomocí prohlížeče je uveden v seznamu konečné zákazníků.  
  
8.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
