---
title: Konfigurace ověření aktivity
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: e6fa043e0a0a96875319d556c19ab8ee90cd2139
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-activity-validation"></a>Konfigurace ověření aktivity
Aktivita ověření umožňuje autorům aktivity a uživatelé identifikovat a zprávy o chybách v konfiguraci aktivity před jeho spuštění. Windows Workflow Foundation (WF) poskytuje následující tři typy ověření aktivity:  
  
-   `RequiredArgument` a `OverloadGroup` atributy.  
  
-   Imperativní ověření založené na kódu.  
  
-   Deklarativní omezení.  
  
 `RequiredArgument` a `OverloadGroup` atributy označuje, že některé argumenty u aktivit je požadovaná. Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a deklarativní omezení povolit ověření o aktivity a jeho relace s obsažený pracovní postup. Pokud aktivita není správně nakonfigurována podle požadavků ověřování, vrátí se chyby ověření a upozornění. Pokud obsažený pracovní postup je vytvořený pomocí návrháře pracovních postupů, všechny chyby ověření a upozornění se zobrazí v návrháři. Pokud pracovní postup je vytvořen mimo návrháře pracovních postupů jsou vráceny všechny chyby ověření při vyvolání pracovního postupu. Bez ohledu na to, jak byl vytvořen pracovní postup nemá nikdy pracovního postupu se chyby ověření provést. Tato část obsahuje přehled těchto typů ověřování aktivity a způsob volání ověření aktivity.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povinné argumenty a skupiny přetížení](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 Popisuje postup použití `RequiredArgument` a `OverloadGroup` atributy pro ověřování.  
  
 [Ověřování na základě imperativního kódu](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 Popisuje, jak používat ověřování založené na kódu <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> na základě aktivity.  
  
 [Deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 Popisuje, jak používat deklarativní omezení pro ověřování komplexní aktivity.  
  
 [Vyvolání ověřování aktivit](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 Popisuje při ověření aktivity se automaticky vyvolá a explicitně vyvolat ověřování.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
