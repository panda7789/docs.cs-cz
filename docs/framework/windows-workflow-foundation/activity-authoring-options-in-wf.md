---
title: Vytváření možnosti aktivity WF
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: f91c74b4e3dc002ed2abf979619b84a81db65e78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516397"
---
# <a name="activity-authoring-options-in-wf"></a>Vytváření možnosti aktivity WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] poskytuje několik možností pro vytváření vlastních aktivit. Požadovanou metodu chcete použít pro danou aktivitu vytváření závisí na jaké běhové funkce jsou vyžadovány.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Při rozhodování o tom, která aktivita se základní třídy na použití pro vytváření vlastních aktivit  
 Následující tabulka uvádí funkce, které jsou dostupné v základních tříd vlastní aktivity.  
  
|Základní aktivitě – třída|Dostupné funkce|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Vytvoří skupiny poskytované systémem a vlastních aktivit do složených aktivit.|  
|<xref:System.Activities.CodeActivity>|Implementuje imperativní funkce tím, že poskytuje <xref:System.Activities.CodeActivity%601.Execute%2A> metoda, která může být přepsána. Také poskytuje přístup k sledování, proměnné a argumenty...|  
|<xref:System.Activities.NativeActivity>|Poskytuje všechny funkce <xref:System.Activities.CodeActivity>, plus přerušení spuštění aktivity, zrušení provedení podřízené aktivity, použití záložek a plánování aktivit, akcí aktivity a funkce.|  
|<xref:System.Activities.DynamicActivity>|Poskytuje DOM jako přístup k vytváření aktivit, které sdílí rozhraní pomocí návrháře WF a běhu stroje prostřednictvím <!--zz <xref:System.ComponentModel.IcustomTypeDescriptor>--> `IcustomTypeDescriptor`, povolení nové aktivity, který se má vytvořit bez definování nových typů.|  
  
## <a name="authoring-activities-using-activity"></a>Vytváření aktivit pomocí aktivity  
 Aktivity, které jsou odvozeny od <xref:System.Activities.Activity> tvoří funkce sestavte jiné existující aktivity. Tyto aktivity mohou být existující vlastní aktivity a aktivity z [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] knihovna aktivit. Ty se tyto aktivity je nejzákladnější způsob, jak vytvořit vlastní funkce. Tento přístup je obvykle provedeny, když pomocí prostředí visual návrhu pro vytváření pracovních postupů.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Vytváření pomocí CodeActivity nebo AsyncCodeActivity aktivity  
 Aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity> nebo <xref:System.Activities.AsyncCodeActivity> můžete implementovat imperativní funkce přepsáním <xref:System.Activities.CodeActivity%601.Execute%2A> metoda s imperativní vlastní kód. Vlastní kód se spustí při spuštění aktivity modulem runtime. Když aktivity vytvořené v tomto případě má přístup k vlastní funkce, že nemáte příslušná oprávnění ke všem funkcím modulu runtime, jako je například úplný přístup k prostředí pro spuštění, umožňuje naplánovat podřízené aktivity, vytvoření záložku nebo podporu pro Zrušit nebo Abort – metoda. Když <xref:System.Activities.CodeActivity> provede, má přístup k snížené verzi prostředí pro spuštění (prostřednictvím <xref:System.Activities.CodeActivityContext> nebo <xref:System.Activities.AsyncCodeActivityContext> třída). Aktivity vytvořené pomocí <xref:System.Activities.CodeActivity> mít přístup k argumentu a proměnná rozlišení, rozšíření a sledování. Plánování asynchronní aktivity lze provést pomocí <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Vytváření pomocí NativeActivity aktivity  
 Aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity>, jako jsou ty, které jsou odvozeny od <xref:System.Activities.CodeActivity>, vytvořit imperativní funkce přepsáním <xref:System.Activities.NativeActivity.Execute%2A>, ale také mají přístup ke všem funkci modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> , který získá předaný do <xref:System.Activities.NativeActivity.Execute%2A> metoda. Tento kontext se podpora pro plánování a zrušení podřízené aktivity, provádění <xref:System.Activities.ActivityAction> a <!--zz <xref:System.Activities.ActivityFunc>--> `ActivityFunc` objekty, průchodu transakce do pracovního postupu, vyvolání asynchronní procesy, zrušení a přerušení spuštění, přístup k provádění vlastnosti a rozšíření a záložky (popisovačů pro opětovné pozastavený pracovní postupy).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Vytváření pomocí DynamicActivity aktivity  
 Na rozdíl od jiných tři typy aktivit, nové funkce nevytvoří odvozením nové typy z <xref:System.Activities.DynamicActivity> (třída je zapečetěná), ale místo toho sloučením funkce do <xref:System.Activities.DynamicActivity.Properties%2A> a <xref:System.Activities.DynamicActivity.Implementation%2A> vlastností pomocí dokument aktivity objektový model (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Vytváření aktivit, které vrácení výsledku  
 Řada aktivit musí vrátit výsledek po jejich provádění. Přestože je možné definovat vlastní vždy <xref:System.Activities.OutArgument%601> na aktivity pro tento účel, doporučuje se místo toho použít <xref:System.Activities.Activity%601>, nebo jsou odvozeny od <xref:System.Activities.CodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>. Každý z těchto základních tříd má <xref:System.Activities.OutArgument%601> s názvem výsledek, který vaši aktivitu můžete použít pro svou vrácenou hodnotu. Aktivity, které vrácení výsledku musí být použit pouze pokud pouze jeden výsledek je nutné vrátit z aktivity; Pokud má být vrácen potřebovat více výsledků, oddělte <xref:System.Activities.OutArgument%601> Členové by měl být místo toho použít.
