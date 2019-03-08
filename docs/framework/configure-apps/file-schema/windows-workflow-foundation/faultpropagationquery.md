---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679356"
---
# <a name="faultpropagationquery"></a>\<faultPropagationQuery>

Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.  Pokaždé, když FaultHandler zpracovává chyby, dojde k této události. Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.

 Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>\
\<sledování > \
\<trackingProfile>\
\<pracovní postup > \
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
|Název aktivity activityName|Řetězec, který určuje název aktivity obslužná rutina chyby, která chybu. Výchozí hodnota je *, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.|
|faultHandlerActivityName|Řetězec, který určuje název aktivity, který byl zdroj chyby.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<faultPropagationQueries>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.  Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.|

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
