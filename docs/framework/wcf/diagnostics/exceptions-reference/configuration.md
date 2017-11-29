---
title: Konfigurace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03881ccef47cab6e7136afbe2a5584b4647fa252
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuration"></a>Konfigurace
Toto téma uvádí všechny výjimky generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] konfigurace.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|Vazba na koncový bod služby se nedá nakonfigurovat.|  
|ConfigElementKeyNull|Klíč elementu specifickou konfiguraci nemůže mít hodnotu null.|  
|ConfigExtensionTypeNotRegisteredInCollection|Typ konkrétní rozšíření není registrován v kolekci konkrétní rozšíření.|  
|ConfigIndexOutOfRange|Hodnota pro konkrétní atribut je mimo rozsah.|  
|ConfigInvalidBindingConfigurationName|Konkrétní konfigurace nemá vazbu s určitým názvem.|  
|ConfigInvalidBindingName|Konkrétní konfigurace nemá vazbu s určitým názvem. Toto je neplatná hodnota pro vazbu.|  
|ConfigInvalidCommonEndpointBehaviorType|Rozšíření konkrétní chování společné chování koncový bod nelze přidat, protože neimplementuje konkrétního typu.|  
|ConfigInvalidCommonServiceBehaviorType|Rozšíření konkrétní chování společné chování služby nelze přidat, protože neimplementuje konkrétního typu.|  
|ConfigInvalidEndpointBehaviorType|Nelze přidat konkrétní chování rozšíření chování konkrétní koncový bod, protože základní typ chování neimplementuje rozhraní IServiceBehavior.|  
|ConfigInvalidExtensionType|Specifický typ musí být odvozený od konkrétní rozšíření, který se má použít v kolekci.|  
|ConfigInvalidServiceBehaviorType|Nelze přidat rozšíření chování, k chování služby s konkrétní název, protože základní typ chování neimplementuje rozhraní IServiceBehavior.|  
|ConfigMessageEncodingAlreadyInBinding|Nelze přidat element kódování konkrétní zprávy. Konkrétní vazba již existuje jiný element kódování zprávy. Může existovat pouze jeden element pro každou vazbu kódování zprávy.|  
|ConfigNoExtensionCollectionAssociatedWithType|Nelze najít rozšíření kolekce přidružené k rozšíření konkrétního typu.|  
|ConfigSectionNotFound|Konkrétní konfiguračního oddílu nelze vytvořit. Souboru Machine.config je chybějící informace. Ověřte, zda je řádně zaregistrován tento konfigurační oddíl a název oddílu, abyste měli správně zadán. Pro Windows Communication Foundation oddíly spustit ServiceModelReg.exe -i odstranění této chyby.|  
|ConfigTransportAlreadyInBinding|Nelze přidat element konkrétní přenosu. Konkrétní vazba již existuje jiný element přenosu. Může existovat pouze jeden element pro každou vazbu kódování zprávy.|
