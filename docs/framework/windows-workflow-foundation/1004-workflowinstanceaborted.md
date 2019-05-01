---
title: 1004 – WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008613"
---
# <a name="1004---workflowinstanceaborted"></a>1004 – WorkflowInstanceAborted

## <a name="properties"></a>Vlastnosti

|||
|-|-|
|ID|1004|
|klíčová slova|WFRuntime|
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
