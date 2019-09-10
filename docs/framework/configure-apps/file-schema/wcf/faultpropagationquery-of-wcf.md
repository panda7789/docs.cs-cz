---
title: <faultPropagationQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855329"
---
# <a name="faultpropagationquery-of-wcf"></a>\<faultPropagationQuery > WCF

Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.  K této události dochází pokaždé, když když FaultHandler zpracovává chybu. Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.

Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**  

## <a name="syntax"></a>Syntaxe

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`faultSourceActivityName`|Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu. Výchozí hodnota je \*, což znamená, že jsou vraceny záznamy o šíření chyb pro všechny aktivity.|
|`faultHandlerActivityName`|Řetězec, který určuje název aktivity, který byl zdroj chyby.|

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.  K této události dochází pokaždé, když když FaultHandler zpracovává chybu.|

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
