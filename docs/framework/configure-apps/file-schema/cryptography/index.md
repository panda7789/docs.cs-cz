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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087997"
---
# <a name="cryptography-settings-schema"></a>Schéma nastavení šifrování
Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses >** ](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry >** ](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidEntry >** ](oidentry-element.md)

|Prvek|Popis|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Obsahuje seznam tříd kryptografie, které mají mapování na popisný název v prvku **\<nameEntry >** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Obsahuje nastavení kryptografie.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Obsahuje mapování tříd na popisné názvy.|  
|[ **\<element > mscorlib** pro nastavení kryptografie](mscorlib-element-for-cryptography-settings.md)|Obsahuje prvek **\<cryptographySettings >** .|  
|[ **\<nameEntry >** ](nameentry-element.md)|Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.|  
|[ **\<oidEntry >** ](oidentry-element.md)|Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.|  
|[ **\<oidMap >** ](oidmap-element.md)|Obsahuje mapování ID ASN. 1 na třídy.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
