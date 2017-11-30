---
title: "Mapování identifikátorů objektů na algoritmy šifrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dbfe394193925e38dad774d39d79ac813abef22a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapování identifikátorů objektů na algoritmy šifrování
Digitální podpisy Ujistěte se, že data není manipulováno při odeslání z jedné aplikace do jiného. Digitální podpis je obvykle počítaný použitím matematické funkce hash data, která mají být podepsané. Při formátování hodnotu hash podepsat, některé algoritmy digitální podpis připojí ASN.1 identifikátor objektu (OID) v rámci operace formátování. Identifikátor OID Určuje algoritmus, který se používá k výpočtu hodnoty hash. Identifikátory objektů rozšířit mechanismus na kryptografické algoritmy vlastní můžete namapovat algoritmy. Následující příklad ukazuje, jak k mapování identifikátor objektu na nový algoritmus hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<Oidentry – > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) obsahuje dva atributy. **OID** atribut je identifikátor objektu. **Název** atribut je hodnota **název** atribut z [ \<nameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Musí existovat mapování z název algoritmu na třídu před identifikátor objektu lze mapovat na jednoduchý název.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
