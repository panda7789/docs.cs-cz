---
title: Konfigurace ověřování aktivit
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 6c971b56e269fbb330bd9ad0a551a9fb9ca01196
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655105"
---
# <a name="configuring-activity-validation"></a>Konfigurace ověřování aktivit
Aktivita ověření umožňuje uživatelům a autoři aktivity k identifikaci a hlášení chyb v konfiguraci aktivity před jeho provedením. Windows Workflow Foundation (WF) obsahuje následující tři typy ověřování aktivit:  
  
- `RequiredArgument` a `OverloadGroup` atributy.  
  
- Imperativní ověřování na základě kódu.  
  
- Deklarativní omezení.  
  
 `RequiredArgument` a `OverloadGroup` atributy označuje, že některé argumenty pro aktivitu je povinný. Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a deklarativní omezení povolit ověřování aktivity a je naznačen vztah se obsažený pracovní postup. Pokud aktivita není správně nakonfigurována podle požadavků na ověření, chyby a upozornění ověření jsou vráceny. Pokud obsažený pracovní postup je vytvořen pomocí návrháře postupu provádění, žádné chyby ověření a upozornění se zobrazí v návrháři. Pokud je pracovní postup vytvořený mimo návrháře postupu provádění všechny chyby ověření jsou vráceny při vyvolání pracovního postupu. Bez ohledu na to, jak sled prací byl vytvořen pracovní postup s chyby ověření nikdy povoleno provádět. Tato část obsahuje přehled těchto typů ověřování aktivit a jak vyvolání ověřování aktivit.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povinné argumenty a skupiny přetížení](required-arguments-and-overload-groups.md)  
 Popisuje způsob použití `RequiredArgument` a `OverloadGroup` atributy pro ověřování.  
  
 [Ověřování na základě imperativního kódu](imperative-code-based-validation.md)  
 Popisuje způsob použití ověřování na základě kódu pro <xref:System.Activities.CodeActivity> a <xref:System.Activities.NativeActivity> podle aktivity.  
  
 [Deklarativní omezení](declarative-constraints.md)  
 Popisuje způsob použití deklarativní omezení pro ověřování komplexní aktivity.  
  
 [Vyvolání ověřování aktivit](invoking-activity-validation.md)  
 Tento článek popisuje při ověřování aktivit je vyvolán automaticky a jak explicitně volat ověření.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
