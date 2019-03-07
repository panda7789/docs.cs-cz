---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485184"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>Vlastnosti

|||
|-|-|
|ID|1004|
|Klíčová slova|WFRuntime|
|úroveň|Informace o|
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|

## <a name="description"></a>Popis

Označuje, že instance pracovního postupu byl zrušen s výjimkou.

## <a name="message"></a>Zpráva

WorkflowInstance Id: '%1' byl zrušen s výjimkou.

## <a name="details"></a>Podrobnosti

|Název položky dat|Datový typ položky|Popis|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|Id instance pracovního postupu|
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimku|
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
