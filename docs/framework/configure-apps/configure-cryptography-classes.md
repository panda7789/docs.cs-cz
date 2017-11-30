---
title: "Konfigurace šifrovacích tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 79eb9f9ef95dae24dd38fa93b137c9303815143b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-cryptography-classes"></a>Konfigurace šifrovacích tříd
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umožňuje správci počítače a nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které používají rozhraní .NET Framework a správně vytvořené aplikace.  Například organizace, která má svou vlastní implementaci kryptografických algoritmů můžete Ujistěte se, že implementace výchozí místo implementace poskytuje [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. I když spravovaných aplikací, které používají šifrování se vždy mohou rozhodnout explicitně vytvořit vazbu na konkrétní implementace, se doporučuje, aby vytvořili kryptografických objekty pomocí kryptografických konfigurační systém.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování názvů algoritmů na třídy šifrování](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Popisuje, jak mapovat název algoritmu šifrování třídu.  
  
 [Mapování identifikátorů objektů na algoritmy šifrování](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Popisuje, jak mapovat identifikátor objektu algoritmus šifrování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)  
 Obsahuje základní informace o kryptografických služeb poskytovaných [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Schéma nastavení šifrování](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Popisuje elementy, které mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.
