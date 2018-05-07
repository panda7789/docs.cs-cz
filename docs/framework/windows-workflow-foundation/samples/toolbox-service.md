---
title: Sada nástrojů služby
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b3ea56d28d202bd8356fea1783b6675a708631d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="toolbox-service"></a>Sada nástrojů služby
Tento příklad ukazuje, jak aktualizovat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sada nástrojů aktivit na základě kontextu pracovního postupu. Ukázka obsahuje pracovní postup, který změní obsah sady nástrojů založené na tom, jestli je vybrané vlastní aktivity.  
  
## <a name="discussion"></a>Diskusní  
 Při vytváření obsahu pracovního postupu, chcete zákazníkům obecně jejich nástrojů jako závislé na kontextu. Uživatel například může chtít zajistit, že sady nástrojů ukazuje několik další aktivity, při přidání konkrétní aktivitu do pracovního postupu. Pokud aktivity budou odebrány z pracovního postupu, by měl sady nástrojů reagují odpovídajícím způsobem v závislosti na požadavcích domény.  
  
 V Návrháři znovu hostovaných pracovních postupů řídit ovládacího prvku sady nástrojů a zajistit, aby na základě změn modelu v pracovním postupu, hostitele spustí potřebné změny v ovládacím prvku panel nástrojů. Ale v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], sady nástrojů není řízené uživateli, a proto je potřeba rozhraní upravit její obsah. `IActivityToolboxService` je tohoto rozhraní.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WorkflowSimulator.sln.  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Otevřete soubor Workflow.xaml.  
  
4.  Přidat **CustomActivity** přetahováním myší z panelu nástrojů. Všimněte si, že volat další sady nástrojů kategorii: **novou kategorii WF** s další aktivitu **přiřadit**.  
  
5.  Nyní zrušte výběr **CustomActivity** tak, že přetáhnete jinou aktivitu do ní.  
  
6.  Položka **přiřadit** v kategorii **novou kategorii WF** v rámci sady nástrojů je teď odebrané. Navíc vzhledem k tomu, že neexistují žádné další položky left v kategorii, bude odebrána také.  
  
7.  Vyberte **CustomActivity** znovu a kategorie a **přiřadit** aktivity je přidány zpět.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
