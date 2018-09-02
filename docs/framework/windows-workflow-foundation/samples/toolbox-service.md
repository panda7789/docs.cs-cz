---
title: Služba sady nástrojů
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406459"
---
# <a name="toolbox-service"></a>Služba sady nástrojů
Tato ukázka předvádí, jak aktualizovat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] panelu nástrojů aktivity na základě kontextu pracovního postupu. Ukázka obsahuje pracovní postup, který změní obsah sady nástrojů založené na tom, jestli je vybraná vlastní aktivity.  
  
## <a name="discussion"></a>Diskuse  
 Při vytváření pracovního postupu, zákazníci chtějí obecně jejich nástrojů být závislá na kontextu. Uživatel může třeba zajistit, že panelu nástrojů zobrazuje několik dalších aktivit, když je konkrétní aktivita přidána do pracovního postupu. Pokud aktivity jsou odebrány z pracovního postupu, by měl panel nástrojů reagovat odpovídajícím způsobem na základě domény požadavků.  
  
 V Návrháři znovu hostovaných pracovních postupů ovládací prvek ovládacího prvku panelu nástrojů a zajistit, aby na základě modelu změn v pracovním postupu, hostitel aktivuje odpovídající změny v ovládacím prvku panel nástrojů. Nicméně v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], panel nástrojů není řízen uživatele a proto je potřeba rozhraní upravte jeho obsah. `IActivityToolboxService` je rozhraní.  
  
 Rozhraní API poskytuje následující čtyři metody.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WorkflowSimulator.sln.  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Otevřete soubor Workflow.xaml.  
  
4.  Přidat **CustomActivity** přetahováním z panelu nástrojů. Všimněte si, že volá další kategorie panelu nástrojů: **novou kategorii WF** pomocí další aktivity **přiřadit**.  
  
5.  Nyní zrušit výběr **CustomActivity** přetáhněte další aktivitu do něj.  
  
6.  Položka **přiřadit** v kategorii **novou kategorii WF** ve skupinovém rámečku panelu nástrojů je odebraná. Navíc vzhledem k tomu, že neexistují žádné další položky v kategorii, bude odebrána také.  
  
7.  Vyberte **CustomActivity** znovu a kategorie a **přiřadit** aktivita je přidána zpět.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
