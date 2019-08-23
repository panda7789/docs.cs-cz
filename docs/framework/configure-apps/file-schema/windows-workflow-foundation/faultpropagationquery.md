---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f77a613f4eb0456a0085096aa478d37c78122217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946305"
---
# <a name="faultpropagationquery"></a>\<faultPropagationQuery>

Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.  K této události dochází pokaždé, když když FaultHandler zpracovává chybu. Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.

 Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>\
\<sledování > \
\<Profil TrackingProfile > \
\<> pracovního postupu \
\<faultPropagationQueries>\
\<faultPropagationQuery>

## <a name="syntax"></a>Syntaxe

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Název aktivity activityName|Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu. Výchozí hodnota je *, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.|
|faultHandlerActivityName|Řetězec, který určuje název aktivity, který byl zdroj chyby.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.  K této události dochází pokaždé, když když FaultHandler zpracovává chybu.|

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
