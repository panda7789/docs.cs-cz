---
title: Schéma nastavení šifrování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 6b6d9eeacb38531ced5768f29bf26de3c9294b71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cryptography-settings-schema"></a>Schéma nastavení šifrování
Schéma nastavení šifrování obsahuje prvky, které určují, jak k mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.  
  
 [**\<Konfigurace >**](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [**\<mscorlib >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [**\<cryptographySettings – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [**\<cryptoNameMapping >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [**\<cryptoClasses – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [**\<cryptoclass – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [**\<nameEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [**\<oidmap – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [**\<oidentry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[**\<cryptoClasses –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do  **\<nameEntry >** element.|  
|[**\<cryptoclass –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Obsahuje třídy šifrování, která má mapování na popisného názvu do  **\<nameEntry >** element.|  
|[**\<cryptographySettings –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|Obsahuje nastavení šifrování.|  
|[**\<cryptoNameMapping –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Obsahuje mapování třídy popisné názvy.|  
|[**\<mscorlib >** element pro nastavení kryptografie](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|Obsahuje  **\<cryptographySettings – >** element.|  
|[**\<nameEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|Mapuje název třídy algoritmus popisný název, který umožňuje jednu třídu k mít mnoho popisné názvy.|  
|[**\<oidentry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|Mapuje ASN.1 identifikátor objektu (OID) popisný název.|  
|[**\<oidmap – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|Obsahuje ASN.1 OID mapování třídy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)
