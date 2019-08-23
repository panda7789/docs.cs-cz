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
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927634"
---
# <a name="cryptography-settings-schema"></a>Schéma nastavení šifrování
Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.  
  
 [ **\<> Konfigurace**](../configuration-element.md)  
  
 [ **\<mscorlib>** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<cryptographySettings >** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping>** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses>** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass>** ](cryptoclass-element.md)  
  
 [ **\<nameEntry >** ](nameentry-element.md)  
  
 [ **\<oidMap>** ](oidmap-element.md)  
  
 [ **\<oidEntry>** ](oidentry-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v  **\<elementu nameEntry >** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Obsahuje třídu kryptografie, která má mapování na popisný název v  **\<elementu nameEntry >** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Obsahuje nastavení kryptografie.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Obsahuje mapování tříd na popisné názvy.|  
|[element > mscorlib pro nastavení kryptografie  **\<** ](mscorlib-element-for-cryptography-settings.md)|Obsahuje element cryptographySettings >.  **\<**|  
|[ **\<nameEntry >** ](nameentry-element.md)|Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.|  
|[ **\<oidEntry>** ](oidentry-element.md)|Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.|  
|[ **\<oidMap>** ](oidmap-element.md)|Obsahuje mapování ID ASN. 1 na třídy.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
