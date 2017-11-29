---
title: "Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94a9ea977d0add14ae9f0c9a889b008b94610ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)
Visual Basic poskytuje snadný způsob můžete nasadit vaše vlastní `My` rozšíření oboru názvů pomocí šablony sady Visual Studio. Pokud vytváříte šablona projektu pro kterou vaše `My` rozšíření jsou nedílnou součástí nového typu projektu, můžete zahrnout pouze vaše vlastní `My` kód rozšíření projektu při exportu šablony. Další informace o exportu šablony projektů najdete v tématu [postupy: vytvoření šablony projektů](/visualstudio/ide/how-to-create-project-templates).  
  
 Pokud vaše vlastní `My` rozšíření je v souboru jednoho kódu, můžete exportovat soubor jako šablonu položky, které můžete přidat uživatele k libovolnému typu projektu jazyka Visual Basic. Následně můžete přizpůsobit šablony položky, chcete-li povolit další funkce a chování pro vaše vlastní `My` rozšíření v projektu jazyka Visual Basic. Tyto funkce patří:  
  
-   Umožňuje uživatelům spravovat vaše vlastní `My` rozšíření **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic.  
  
-   Automatické přidávání vašich vlastních `My` příponu při odkaz na zadaná sestavení je přidat do projektu.  
  
-   Skrytí `My` rozšíření šablony položky v **přidat položku** dialogu tak, aby není zahrnutý v seznamu položek projektu.  
  
 Toto téma popisuje, jak zabalit vlastní `My` rozšíření jako šablonu skrytá položka, kterou je možné spravovat z **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic. Vlastní `My` rozšíření můžete také přidat automaticky při přidání odkazu na zadaná sestavení do projektu.  
  
## <a name="create-a-my-namespace-extension"></a>Vytvoření rozšíření oboru názvů My  
 Prvním krokem při vytváření balíčku pro nasazení pro vlastní `My` rozšíření je pro vytvoření rozšíření jako soubor jednoho kódu. Podrobnosti a pokyny o tom, jak vytvořit vlastní `My` rozšíření, najdete v části [rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Export rozšíření oboru názvů My jako šablonu položky  
 Až budete mít soubor kód, který zahrnuje vaše `My` rozšíření oboru názvů, můžete exportovat soubor kódu jako šablonu položky Visual Studio. Pokyny o tom, jak exportovat soubor jako šablonu položky Visual Studio najdete v tématu [postupy: vytváření šablon položek](/visualstudio/ide/how-to-create-item-templates).  
  
> [!NOTE]
>  Pokud vaše `My` rozšíření oboru názvů má závislost na určitém sestavení, můžete upravit položku šablony můžete automaticky nainstalovat vaší `My` rozšíření oboru názvů, pokud je přidán odkaz na sestavení. Výsledkem je budete chtít vyloučit tento odkaz na sestavení, při exportu souboru kódu jako šablonu položky Visual Studio.  
  
## <a name="customize-the-item-template"></a>Přizpůsobení šablony položek  
 Můžete povolit šabloně položka pro správu z **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic. Můžete také povolit šablonu položky pro automaticky přidá, když je odkaz na zadaná sestavení přidat do projektu. Pokud chcete povolit toto vlastní nastavení, přidáte nového souboru s názvem souboru CustomData do šablony a poté přidejte nový element jazyka XML v souboru .vstemplate.  
  
### <a name="add-the-customdata-file"></a>Přidejte soubor CustomData  
 CustomData soubor je textový soubor, který má příponu názvu souboru. CustomData (název souboru lze nastavit na jakoukoli hodnotu smysluplnou) a který obsahuje XML. Kód XML v souboru CustomData dá pokyn, Visual Basic pro zahrnutí vaše `My` rozšíření uživatelům při používání **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic. Volitelně můžete přidat <`AssemblyFullName>` atribut CustomData souboru XML. Tím se nastaví jazyka Visual Basic můžete automaticky nainstalovat vaše vlastní `My` příponu při odkaz na konkrétní sestavení se přidá do projektu. Můžete použít k vytvoření souboru CustomData žádné textového editoru nebo editoru XML a poté jej přidejte do šablony položky komprimované složce (.zip soubor).  
  
 Například následující kód XML zobrazí obsah souboru CustomData, který se přidá šablonu položky do složky Moje rozšíření v projektu jazyka Visual Basic, když odkaz na sestavení Microsoft.VisualBasic.PowerPacks.Vs.dll se přidá do projektu.  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 Obsahuje soubor CustomData <`VBMyExtensionTemplate>` element, který má atributy uvedené v následující tabulce.  
  
|Atribut|Popis|  
|---|---|  
|`ID`|Požadováno. Jedinečný identifikátor pro rozšíření. Pokud rozšíření, která má toto ID již byla přidána do projektu, uživatel nebude vyzván ji znovu přidejte.|  
|`Version`|Požadováno. Číslo verze šablony položky.|  
|`AssemblyFullName`|Volitelné. Název sestavení. Když odkaz na toto sestavení se přidá do projektu, uživatel bude vyzváni k přidání `My` rozšíření z této šablony položky.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Přidat \<CustomDataSignature > elementu, který chcete soubor .vstemplate  
 K identifikaci vaší šablony položek sady Visual Studio `My` rozšíření oboru názvů, musíte také upravit soubor .vstemplate položky šablony. Je nutné přidat `<CustomDataSignature>` elementu, který chcete `<TemplateData>` elementu. `<CustomDataSignature>` Element musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Soubory v komprimované složce (.zip soubor) nelze upravovat přímo. Musíte zkopírovat soubor .vstemplate z komprimované složky, upravte ho a potom můžete nahradit soubor .vstemplate v komprimované složce aktualizovanou kopií.  
  
 Následující příklad ukazuje obsah .vstemplate soubor, který má `<CustomDataSignature>` elementu přidány.  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a>Instalace šablony  
 Instalace šablony, můžete zkopírovat komprimované složce (.zip soubor) do složky šablon položek jazyka Visual Basic (například Dokumenty\visual 2008\Templates\Item Templates\Visual Basic). Alternativně můžete publikovat šablony jako soubor Instalační program Visual Studio (.vsi).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Přizpůsobení výběru objektů jsou k dispozici v mé](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
