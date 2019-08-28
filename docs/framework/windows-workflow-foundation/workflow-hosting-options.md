---
title: Možnosti hostování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 4eaed147f312f3963aa1ca1d4f5dbe010c4189ad
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037822"
---
# <a name="workflow-hosting-options"></a>Možnosti hostování pracovního postupu
Většina ukázek programovací model Windows Workflow Foundation (WF) používá pracovní postupy, které jsou hostovány v konzolové aplikaci, ale toto není reálný scénář pro reálné pracovní postupy. Pracovní postupy v skutečných obchodních aplikacích se budou hostovat v trvalých procesech – buď pomocí služby systému Windows, kterou vytvořil vývojář, nebo na serverovou aplikaci, jako je IIS 7,0 nebo AppFabric. Rozdíly mezi těmito přístupy jsou následující.

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hostování pracovních postupů ve službě IIS pomocí technologie Windows AppFabric

Používání služby IIS s AppFabric je upřednostňovaným hostitelem pro pracovní postupy. Hostitelská aplikace pro pracovní postupy využívající rozhraní AppFabric je aktivační služba systému Windows, která odebere závislost na samotném HTTP prostřednictvím služby IIS.

## <a name="hosting-workflows-in-iis-alone"></a>Hostování pracovních postupů pouze v rámci služby IIS

Použití samotného IIS 7,0 se nedoporučuje, protože jsou k dispozici nástroje pro správu a monitorování pro technologii AppFabric, která usnadňuje údržbu spuštěných aplikací. Pracovní postupy by se měly hostovat jenom v rámci služby IIS 7,0, pokud se při přechodu na AppFabric nesouvisí s infrastrukturou.

> [!WARNING]
> Služba IIS 7,0 recykluje fondy aplikací pravidelně z různých důvodů. Po recyklaci fondu aplikací přestane služba IIS přijímat zprávy do starého fondu a vytvoří instance nového fondu aplikací, aby přijímala nové žádosti. Pokud pracovní postup pokračuje v práci i po odeslání odpovědi, IIS 7,0 nebude vědět o dokončené práci a může recyklovat fond hostitelských aplikací. Pokud k tomu dojde, bude pracovní postup přerušen a služba sledování zaznamená zprávu [1004-WorkflowInstanceAborted](1004-workflowinstanceaborted.md) s prázdným polem důvod.
>
> Pokud se použije trvalost, hostitel musí explicitně restartovat přerušené instance z posledního bodu trvalosti.
>
> Pokud se používá technologie AppFabric, služba správy pracovního postupu nakonec obnoví pracovní postup z posledního úspěšného bodu trvalosti, pokud se použije trvalost. Pokud se nepoužije žádná trvalá a pracovní postup provádí operace mimo vzor požadavků a odpovědí, data se po přerušení pracovního postupu ztratí.

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hostování pracovního postupu ve vlastní službě systému Windows

Vytvořením vlastní služby pracovního postupu pro hostování pracovního postupu bude vyžadovat, aby vývojář duplikoval spoustu funkcí poskytovaných službou AppFabric, ale umožní vám pružnější práci s vlastními funkcemi. Tato možnost by měla být zvážena pouze v případě, že se technologie AppFabric ukáže jako možnost.
