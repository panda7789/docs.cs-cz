---
title: Možnosti při vytváření aktivit v WF
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 219d759cd1390a83abfb90af509b21047085f6e9
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697669"
---
# <a name="activity-authoring-options-in-wf"></a>Možnosti při vytváření aktivit v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] poskytuje několik možností, jak k tvorbě vlastních aktivit. Správný způsob, kterým pro danou aktivitu vytváření závisí na funkcích za běhu se vyžadují.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Rozhodování o tom, jaké aktivity základní třídy na použití pro vytváření vlastních aktivit  
 V následující tabulce jsou uvedeny funkce dostupné v základních třídách vlastní aktivity.  
  
|Třída základní aktivity|Funkce, které jsou k dispozici|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Vytvoří skupiny poskytované systémem a vlastních aktivit do složené aktivity.|  
|<xref:System.Activities.CodeActivity>|Implementuje funkce imperativní tím, že poskytuje <xref:System.Activities.CodeActivity%601.Execute%2A> metodu, která se dá přepsat. Také poskytuje přístup ke sledování, proměnné a argumenty...|  
|<xref:System.Activities.NativeActivity>|Poskytuje všechny funkce <xref:System.Activities.CodeActivity>, plus přerušení provádění aktivity, zrušení podřízené aktivity spuštění, použití záložek a plánování aktivit, aktivit akce a funkce.|  
|<xref:System.Activities.DynamicActivity>|Poskytuje modelu DOM jako přístup k vytváření aktivit, které sdílí rozhraní pomocí Návrháře pracovního postupu a za běhu strojů prostřednictvím <xref:System.ComponentModel.ICustomTypeDescriptor>, umožňuje nové aktivity, který se má vytvořit bez definování nových typů.|  
  
## <a name="authoring-activities-using-activity"></a>Použití aktivity aktivit autorizace  
 Aktivity, které jsou odvozeny z <xref:System.Activities.Activity> compose funkce sloučením další existujících aktivit. Tyto aktivity mohou být existující vlastní aktivity a aktivit [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] knihovny aktivit. Tyto aktivity sestavení je nejzákladnější možnost pro vytvoření vlastní funkce. Tento přístup se nejčastěji používá při použití prostředí pro vizuální návrh pro vytváření pracovních postupů.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Vytváření pomocí CodeActivity nebo AsyncCodeActivity aktivity  
 Aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity> nebo <xref:System.Activities.AsyncCodeActivity> můžete implementovat imperativní funkce tak, že přepíšete <xref:System.Activities.CodeActivity%601.Execute%2A> metodu s vlastní imperativního kódu. Vlastní kód se spustí, když modul runtime při spuštění této aktivity. Aktivity vytvořené tímto způsobem mají přístup k vlastní funkce, že nemáte příslušná oprávnění ke všem funkcím modulu runtime, jako je úplný přístup k prostředí pro spuštění, možnosti plánovat podřízené aktivity, vytváření záložek nebo podporu pro Zrušit nebo přerušení metody. Když <xref:System.Activities.CodeActivity> spustí, má přístup k nižší verzi prostředí pro spuštění (prostřednictvím <xref:System.Activities.CodeActivityContext> nebo <xref:System.Activities.AsyncCodeActivityContext> třídy). Aktivity vytvořené pomocí <xref:System.Activities.CodeActivity> mají přístup k argumentu a proměnná rozlišení, rozšíření a sledování. Plánování asynchronní aktivity lze provést pomocí <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Vytváření aktivit pomocí NativeActivity  
 Aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity>, jako jsou ty, které jsou odvozeny z <xref:System.Activities.CodeActivity>, vytvořit imperativní funkce tak, že přepíšete <xref:System.Activities.NativeActivity.Execute%2A>, ale také mají přístup ke všem funkce modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> , který získá předán <xref:System.Activities.NativeActivity.Execute%2A> metody. Tento kontext zahrnuje podporu pro plánování a pro zrušení podřízené aktivity, provádění <xref:System.Activities.ActivityAction> a <xref:System.Activities.ActivityFunc%601> objekty, tok transakcí do pracovního postupu, volání asynchronních procesů, zrušení a přeruší provádění, přístup k provádění vlastnosti a rozšíření a záložky (obslužné rutiny pro obnovení pozastavené pracovní postupy).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Vytváření aktivit pomocí dynamické aktivity  
 Na rozdíl od jiných tři typy aktivit, nové funkce nevytvoří odvozením nové typy z <xref:System.Activities.DynamicActivity> (zapečetěné třídy), ale místo toho sloučením funkce do <xref:System.Activities.DynamicActivity.Properties%2A> a <xref:System.Activities.DynamicActivity.Implementation%2A> vlastností pomocí dokument aktivity objektový model (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Vytváření aktivit, které vrací výsledek  
 Řada aktivit musí vracet výsledek po jejich spuštění. I když je vždy definovat vlastní <xref:System.Activities.OutArgument%601> na aktivitu pro tento účel, doporučuje se místo toho použijte <xref:System.Activities.Activity%601>, nebo jsou odvozeny z <xref:System.Activities.CodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>. Každá z těchto základních tříd má <xref:System.Activities.OutArgument%601> s názvem výsledek, který vaši aktivitu můžete použít jeho návratovou hodnotu. Aktivity, které vrací výsledek lze používat pouze pokud pouze jeden výsledek musí být vrácena z aktivity; Pokud potřebujete vrátit více výsledků, oddělte <xref:System.Activities.OutArgument%601> členy by místo toho používat.
