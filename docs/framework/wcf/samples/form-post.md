---
title: Zpracování odeslaného formuláře
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 9115b9abfa7039bf409bb9bbce54e5012d05a074
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44077012"
---
# <a name="form-post"></a>Zpracování odeslaného formuláře
Tato ukázka předvádí, jak rozšířit programovací model REST WCF pro podporu nové formáty příchozí žádosti. Ukázka také zahrnuje implementace formátovací modul, který může deserializovat požadavek z odeslaného formuláře HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Kromě toho Ukázka používá šablonu T4 obnovíte stránku HTML, který poskytuje formulář HTML, který uživatelé mohou publikovat zpět ve službě WCF REST.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Rozšíření podpory pro příchozí požadavek formáty.  
  
-   Integrace šablony T4.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad se skládá ze dvou projektů. Jeden projekt je HtmlFormProcessing knihovnu, která obsahuje vlastní požadavek formátovací modul, který může deserializovat příspěvky formuláře HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy. Druhý projekt je konzolová aplikace, která rozšiřuje ukázka základní služby prostředků použít vlastní požadavek formátovací modul HtmlFormProcessing knihovny.  
  
 Vlastní formátovací modul, který může deserializovat příspěvky formuláře HTML (HtmlFormRequestDispatchFormatter) přijímá obě [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které je možné převést z řetězce pomocí <xref:System.ServiceModel.Dispatcher.QueryStringConverter> a typy označeny pomocí <xref:System.Runtime.Serialization.DataContractAttribute> , které mají pouze členové, které mohou být převést z řetězce QueryStringConverter.  
  
 Projekt knihovny HtmlFormProcessing zahrnuje také abstraktní základní třídu, `RequestBodyDispatchFormatter`, které je možné vytvořit další vlastní žádost o formátování. Odvozování z `RequestBodyDispatchFormatter` umožňuje vývojářům soustředit se na žádosti subjektu deserializace logika, která umožňuje základní třídu pro mapování parametry šablona identifikátoru URI k parametrům metody operace. V knihovně HtmlFormProcessing projektu je také `HtmlFormProcessingBehavior` třídu, která ukazuje, jak jsou odvozeny z <xref:System.ServiceModel.Description.WebHttpBehavior> nahraďte vlastní požadavek formátování výchozí žádost o formátování.  
  
 Tento projekt konzolové aplikace rozšiřuje [služba základních prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) vzorku. Ukázka základní služby prostředků ukazuje, jak vystavit prostředek způsobem, který využívá programovací model REST WCF. V ukázce služba základních prostředků je prostředek kolekce zákazníka přístupný tak, aby zákazníci v kolekci můžete vytvořit, načíst, aktualizovat a odstranit. Ukázka služby na úrovni Basic prostředků používá pouze dva nativně podporované příchozí požadavek formáty, XML a JSON.  
  
 Aplikace konzoly v této ukázce Post formuláře využívá vlastní formátovací modul v knihovně HtmlFormProcessing, což umožňuje uživatelům vytvářet zákazníkům odesláním požadavku z odeslaného formuláře HTML v prohlížeči. Přidá také operace, která vrátí stránku HTML, který obsahuje formulář, který se má publikovat zpět do služby. Tato stránka HTML je generována pomocí předzpracovaná šablona T4, který se skládá z .tt soubor a soubor automaticky generované .cs. Soubor .tt umožňuje vývojáři psát odpovědi ve formě šablony, který obsahuje proměnné a řídit struktury. Další informace o šablonách T4 naleznete v tématu [generování artefakty podle pomocí textových šablon](https://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro ukázku Post formuláře. Při spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce a spusťte ukázku úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a zvolením "Spustit jako správce" v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a pak stisknutím kombinace kláves CTRL + F5 spusťte FormPost projekt konzolové aplikace.  
  
3.  V okně konzoly se zobrazí a poskytuje URI spuštěnou službu a stránku pro spuštěnou službu identifikátoru URI HTML s nápovědou.  
  
4.  Při spuštění ukázky, klient zapíše stavu aktuální aktivity, jestli se nějakým zákazníka, aktualizuje se zákazník, odstranění zákazníka nebo získáním seznamu aktuální zákazníci ze služby do okna konzoly.  
  
5.  Zobrazí se výzva k procházení k identifikátoru URI zákazníka formuláře. Otevřete prohlížeč a přejděte do daného identifikátoru URI. Zadejte název a adresa zákazníka a kliknutím **odeslat** tlačítko.  
  
6.  Stisknutím jakékoli klávesy pokračoval ukázkové okna konzoly.  
  
7.  Jako ukázku dokončí, Všimněte si, že zákazník, který jste vytvořili pomocí prohlížeče součástí konečný seznam zákazníků.  
  
8.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
