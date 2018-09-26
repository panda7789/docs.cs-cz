---
title: Schéma nastavení šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 71d2edac1dd9a84c9d3c92049d2494c7c5bd54b0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216341"
---
# <a name="cryptography-settings-schema"></a>Schéma nastavení šifrování
Schéma nastavení šifrování obsahuje elementy, které určují způsob mapování popisné názvy algoritmů tříd, které implementují algoritmy šifrování.  
  
 [**\<Konfigurace >**](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [**\<mscorlib >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [**\<cryptographySettings – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [**\<cryptoNameMapping >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [**\<cryptoClasses – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [**\<cryptoclass – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [**\<nameEntry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [**\<oidmap – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [**\<oidentry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[**\<cryptoClasses –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování  **\<nameEntry >** elementu.|  
|[**\<cryptoclass –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Obsahuje kryptografickou třídu, která nemá mapování na popisný název v  **\<nameEntry >** elementu.|  
|[**\<cryptographySettings –**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|Obsahuje nastavení šifrování.|  
|[**\<cryptoNameMapping**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Obsahuje mapování tříd pro popisné názvy.|  
|[**\<mscorlib >** – element pro nastavení kryptografie](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|Obsahuje  **\<cryptographySettings – >** elementu.|  
|[**\<nameEntry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.|  
|[**\<oidentry – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|Identifikátor objektu (OID) ASN.1 se mapuje na popisný název.|  
|[**\<oidmap – >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|Obsahuje mapování ASN.1 OID pro třídy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)
