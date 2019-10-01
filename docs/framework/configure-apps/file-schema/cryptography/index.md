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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699806"
---
# <a name="cryptography-settings-schema"></a>Schéma nastavení šifrování
Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<oidEntry >** ](oidentry-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ **@no__t – 2cryptoClasses**>](cryptoclasses-element.md)|Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku **\<nameEntry >** .|  
|[ **@no__t – 2cryptoClass**>](cryptoclass-element.md)|Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .|  
|[ **@no__t – 2cryptographySettings**>](cryptographysettings-element.md)|Obsahuje nastavení kryptografie.|  
|[ **@no__t – 2cryptoNameMapping**>](cryptonamemapping-element.md)|Obsahuje mapování tříd na popisné názvy.|  
|[ **@no__t – element > 2mscorlib** pro nastavení kryptografie](mscorlib-element-for-cryptography-settings.md)|Obsahuje prvek **> \<cryptographySettings** .|  
|[ **@no__t – 2nameEntry >** ](nameentry-element.md)|Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.|  
|[ **@no__t – 2oidEntry >** ](oidentry-element.md)|Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.|  
|[ **@no__t – 2oidMap >** ](oidmap-element.md)|Obsahuje mapování ID ASN. 1 na třídy.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
