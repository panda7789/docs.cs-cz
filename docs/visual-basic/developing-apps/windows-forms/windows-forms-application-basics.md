---
title: "Základy formulářové aplikace Windows (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c5355f10fba2d1d18bc514c93f31051781bed14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-application-basics-visual-basic"></a>Základy formulářové aplikace Windows (Visual Basic)
Důležitou součástí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je schopnost vytvářet aplikace Windows Forms, které běží místně na počítačích uživatelů. Visual Studio můžete použít k vytvoření aplikace a uživatelské rozhraní Windows Forms pomocí. Aplikace Windows Forms jsou založeny na třídy z <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="designing-windows-forms-applications"></a>Navrhování Windows Forms aplikace  
 Můžete vytvořit Windows Forms a aplikace služby systému Windows s [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]. Další informace naleznete v následujících tématech:  
  
-   [Začínáme s Windows Forms](https://msdn.microsoft.com/library/ms229601.aspx). Poskytuje informace o tom, jak vytvořit a program Windows Forms.  
   
-   [Ovládací prvky Windows Forms](https://msdn.microsoft.com/library/ettb6e2a.aspx). Kolekce témat s podrobnostmi o použití ovládacích prvků Windows Forms.  
  
-   [Aplikace služby systému Windows](https://msdn.microsoft.com/library/y817hyb6.aspx). Seznam témat, která popisují, jak vytváření služeb systému Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Sestavování bohaté, interaktivní uživatelské rozhraní  
 Windows Forms je komponenta čipové klienta [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], sadu spravovaných knihovny, které umožňují běžné úkoly aplikace jako čtení a zápis do systému souborů. Použití vývojového prostředí jako [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], můžete vytvořit Windows Forms aplikace, které zobrazují informace, žádají vstup od uživatele a komunikaci se vzdálenými počítači přes síť.  
  
 V systému Windows Forms formulář je visual prostor, na kterém je zobrazit informace o uživateli. Běžně vytváříte aplikace Windows Forms podle umístění ovládacích prvků ve formulářích a vývoj odpovědi na akce uživatele, jako je například kliknutí myší nebo stisknutí klávesy. A *řízení* je element diskrétní uživatelské rozhraní (UI), který zobrazuje data nebo přijímá data vstup.  
  
### <a name="events"></a>Události  
 Když uživatel provede něco do svého formuláře nebo jeden z jeho ovládacích prvků, vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, když k nim dojde. Další informace najdete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx).  
  
### <a name="controls"></a>Ovládací prvky  
 Windows Forms obsahuje řadu ovládacích prvků, které můžete umístit na formulářích: ovládací prvky, které zobrazují textová pole, tlačítka, rozevírací seznamy, přepínače a i webové stránky. Seznam všech ovládacích prvků, můžete použít ve formuláři najdete v tématu [ovládací prvky používané ve formulářích Windows](https://msdn.microsoft.com/library/3xdhey7w.aspx). Pokud ovládací prvek existující nevyhovuje vašim potřebám, Windows Forms také podporuje, vytváření vlastní vlastních ovládacích prvků pomocí <xref:System.Windows.Forms.UserControl> třídy.  
  
 Windows Forms má bohaté ovládací prvky uživatelského rozhraní, které emulují funkce v vyšší kategorie aplikace, jako je Microsoft Office. Pomocí <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip> ovládací prvek, můžete vytvořit panely nástrojů a nabídky, které obsahují text, obrázky, zobrazují podnabídky a hostovat další ovládací prvky, jako je například textová pole a pole se seznamem.  
  
 Pomocí [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Návrhář formulářů přetahování myší, můžete snadno vytvořit formulářových aplikací Windows: právě ovládací prvky s ukazatelem pro výběr a umístit je na místo na formuláři. Návrhář poskytuje nástroje, jako je například mřížky a "snap řádky" provést starostí zarovnání ovládacích prvků. A zda používáte [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] nebo kompilace v příkazovém řádku, můžete použít <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> a <xref:System.Windows.Forms.SplitContainer> ovládací prvky pro vytvoření pokročilých rozložení s minimální čas a úsilí na formulářích.  
  
### <a name="custom-ui-elements"></a>Vlastní prvky uživatelského rozhraní  
 Nakonec, pokud je nutné vytvořit vlastní vlastní elementy uživatelského rozhraní <xref:System.Drawing> obor názvů obsahuje všechny třídy, které potřebujete k vykreslení čar, kružnice a ostatním tvarům přímo na formuláři.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytvořte novou aplikaci Windows Forms s[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]|[Návod: Vytvoření jednoduché Windows Form](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Použití ovládacích prvků ve formulářích|[Postupy: Přidání ovládacích prvků do formulářů Windows](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|Vytváření grafiky s<xref:System.Drawing>|[Začínáme s programováním grafiky](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|Vytvořit vlastní ovládací prvky|[Postupy: dědění ze třídy UserControl](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>Zobrazení a manipulace s daty  
 Mnoho aplikací musí zobrazit data z databáze, soubor XML, webové služby XML nebo jiný zdroj dat. Windows Forms poskytuje flexibilní ovládací <xref:System.Windows.Forms.DataGridView> řízení pro vykreslení tabulkových data v tradiční řádků a sloupců formátu, tak, aby každá část data nacházela vlastní buňku. Pomocí <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled jednotlivých buněk, zamknout libovolný řádků a sloupců v místě a zobrazit komplexní ovládacích prvků do buněk mezi další funkce.  
  
 Připojení ke zdrojům dat přes síť je jednoduchou úlohou s inteligentní klienti Windows Forms. <xref:System.Windows.Forms.BindingSource> Součásti nové s Windows Forms v [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] a [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], představuje připojení ke zdroji dat a poskytuje metody pro vytvoření vazby dat s ovládacími prvky navigace na předchozí a další záznamy, úpravy záznamů a ukládání změny zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje jednoduché rozhraní přes <xref:System.Windows.Forms.BindingSource> součásti přechody mezi záznamy.  
  
### <a name="data-bound-controls"></a>Ovládací prvky vázané na data  
 Můžete vytvořit ovládací prvky vázané na data snadno pomocí okna zdroje dat, která zobrazuje zdroje dat, jako je například databáze, webové služby a objekty ve vašem projektu. Ovládací prvky vázané na data můžete vytvořit tak, že přetáhnete položky z tohoto okno do formuláře ve vašem projektu. Vám může také navázat existujících ovládacích prvků k datům přetažením objektů z okna zdroje dat do existujícího ovládacího prvku.  
  
### <a name="settings"></a>Nastavení  
 Jiný typ vazby dat, které můžete spravovat ve Windows Forms, jsou nastavení. Většina inteligentních klientských aplikací musí zachovat určité informace o jejich stavu spuštění, jako je například velikost poslední známá formulářů a zachovat data předvolba uživatele, například výchozí umístění pro ukládání souborů. Funkce nastavení aplikace řeší tyto požadavky tím, že poskytuje snadný způsob, jak uložit oba typy nastavení v klientském počítači. Jednou definované pomocí [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] nebo editor kódu, tato nastavení jsou nastavené jako trvalé jako XML a automaticky načíst zpět do paměti v době běhu.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Použití <xref:System.Windows.Forms.BindingSource> součásti|[Postupy: vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí návrháře](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|Práce s [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zdroje dat|[Postupy: řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Použití okna zdroje dat|[Návod: Zobrazování dat ve formuláři Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Nasazení aplikací na klientských počítačích  
 Jakmile jste napsali vaší aplikace, je nutné ji odeslat uživatelům, aby můžete nainstalovat a spustit ji v klientských počítačích. Pomocí [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] technologie, můžete nasadit v rámci aplikace z [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] nástrojem pomocí několika kliknutí a uživatelům poskytnout adresu URL odkazující na aplikaci na webu. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]spravuje všechny elementy a závislosti v aplikaci a zajistí, že je aplikace správně nainstalovat na klientském počítači.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]aplikace může být nakonfigurována, spustit pouze když je uživatel připojený k síti, nebo pokud online nebo offline. Pokud určíte, že aplikace má podporovat offline operace [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] přidá odkaz na aplikaci v uživatele **spustit** nabídky, takže uživatel může otevřít bez pomocí adresy URL.  
  
 Při aktualizaci aplikace, můžete publikovat nový manifest nasazení a novou kopii aplikace na vašem webovém serveru. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]zjistí, že je k dispozici aktualizace a upgrady instalace uživatele; žádné další programování se vyžaduje k aktualizaci původního sestavení.  
  
 Pro úplnou Úvod do [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], najdete v části [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Nasazení aplikace s[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizace [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nasazení|[Postupy: Správa aktualizací pro aplikaci ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Správa zabezpečení s[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Další ovládací prvky a funkce  
 Existuje mnoho dalších funkcí ve Windows Forms, který implementující běžné úlohy rychlý a snadný, jako je podpora pro vytváření dialogových oken, tisk, přidání nápovědy a dokumentace a lokalizace aplikace pro více jazyků. Kromě toho využívá robustní zabezpečení systému Windows Forms [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], který vám umožňuje vytváření bezpečnější aplikací pro vaše zákazníky.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytiskne obsah formuláře|[Postupy: tisk grafiky ve Windows Forms](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [Postupy: Tisk vícestránkového textového souboru v systému Windows Forms](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|Další informace o zabezpečení Windows Forms|[Zabezpečení ve Windows Forms – přehled](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Přehled produktu Windows Forms](https://msdn.microsoft.com/library/8bxxy49h.aspx)  
 [My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
