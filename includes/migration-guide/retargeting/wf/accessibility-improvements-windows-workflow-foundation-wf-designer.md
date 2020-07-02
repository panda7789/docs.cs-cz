---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614556"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a>Vylepšení usnadnění v Návrháři pracovního postupu programovací model Windows Workflow Foundation (WF)

#### <a name="details"></a>Podrobnosti

Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF) vylepšuje, jak funguje s technologiemi usnadnění. Tato vylepšení zahrnují následující změny:

- Pořadí karet se změní na zleva doprava a shora dolů v některých ovládacích prvcích:
- Okno Inicializace korelace pro nastavení dat korelace pro <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu
- Okno Definice obsahu pro <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> aktivity,, a <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply>
- Další funkce jsou k dispozici prostřednictvím klávesnice:
- Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny klávesnicí při prvním zaměření.
- Ikony upozornění jsou teď dostupné pomocí klávesnice.
- Tlačítko Další vlastnosti v okno Vlastnosti je teď dostupné pomocí klávesnice.
- Uživatelé s klávesnicí teď mají přístup k položkám záhlaví v podoknech argumenty a proměnné Návrhář postupu provádění.
- Vylepšená viditelnost položek s fokusem, například když:
- Přidávání řádků do datových mříží používaných návrháři Návrhář postupu provádění a aktivit.
- Procházení polí v <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> aktivitách a
- Nastavení výchozích hodnot pro proměnné nebo argumenty
- Čtečky obrazovky teď můžou správně rozpoznat:
- Zarážky nastavené v Návrháři postupu.
- <xref:System.Activities.Statements.FlowSwitch%601>Aktivity, <xref:System.Activities.Statements.FlowDecision> a <xref:System.ServiceModel.Activities.CorrelationScope> .
- Obsah <xref:System.ServiceModel.Activities.Receive> aktivity
- Cílový typ <xref:System.Activities.Statements.InvokeMethod> aktivity.
- Pole se seznamem výjimek a oddíl finally v <xref:System.Activities.Statements.TryCatch> aktivitě.
- Pole se seznamem typ zprávy, rozdělovač v okně Přidat Inicializátory korelace, okno Definice obsahu a okno Vlastnosti CorrelatesOn definice v aktivitách zasílání zpráv (,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> ).
- Cíle přechodů a přechodů stavového stroje.
- Poznámky a konektory v <xref:System.Activities.Statements.FlowDecision> aktivitách.
- Místní nabídky pro aktivity v kontextu (klikněte pravým tlačítkem myši).
- Editor hodnot vlastností, tlačítko Vymazat hledání, kategorie podle abecedy a abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.
- Procento přiblížení v Návrhář postupu provádění.
- Oddělovač v rámci <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.
- <xref:System.Activities.Statements.InvokeDelegate>Aktivita.
- Okno vybrat typy pro aktivity slovníku ( `Microsoft.Activities.AddToDictionary&lt;TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>` atd.).
- Okno Procházet a vybrat typ .NET.
- Popis cesty v Návrhář postupu provádění.
- Uživatelé, kteří si zvolí Vysoký kontrast Themes, uvidí mnoho vylepšení viditelnosti Návrhář postupu provádění a jeho ovládací prvky, jako je lepší poměr kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.

#### <a name="suggestion"></a>Návrh

Pokud máte aplikaci s novým hostovaným návrhářem pracovních postupů, může vaše aplikace tyto změny využít provedením některé z těchto akcí:

- Zkompilujte aplikaci a Zaměřte se na .NET Framework 4.7.1. Tyto změny přístupnosti jsou ve výchozím nastavení povolené.
- Pokud je vaše aplikace cílena na .NET Framework 4,7 nebo starší, ale běží na .NET Framework 4.7.1, můžete si z těchto starších chování přístupnosti přidat následující app.config [přepínač AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` a nastavit ji na `false` , jak ukazuje následující příklad.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |
