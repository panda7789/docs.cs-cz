---
title: Mapování identifikátorů objektů na algoritmy šifrování
description: Podívejte se, jak namapovat identifikátor objektu (OID) na kryptografický algoritmus v rozhraní .NET pomocí prvků oidEntry a nameEntry v konfiguračním souboru XML.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142001"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapování identifikátorů objektů na algoritmy šifrování
Digitální podpisy zajišťují, že při posílání z jednoho programu do druhého se data neúmyslně nezměnila. Digitální podpis se obvykle počítá použitím matematické funkce na hodnotu hash dat, která mají být podepsána. Při formátování hodnoty hash, která má být podepsána, některé algoritmy digitálního podpisu připojí jako součást operace formátování identifikátor objektu ASN. 1 (OID). Identifikátor OID identifikuje algoritmus, který se použil k výpočtu hodnoty hash. Můžete mapovat algoritmy na identifikátory objektů a roztáhnout mechanismus kryptografie na použití vlastních algoritmů. Následující příklad ukazuje, jak namapovat identifikátor objektu na nový algoritmus hash.  
  
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
  
 [ \<oidEntry> Element](./file-schema/cryptography/oidentry-element.md) obsahuje dva atributy. Atribut **OID** je číslo identifikátoru objektu. Atribut **Name** je hodnota atributu **Name** z [ \<nameEntry> elementu](./file-schema/cryptography/nameentry-element.md). Aby bylo možné mapovat identifikátor objektu na jednoduchý název, musí být mapování z názvu algoritmu na třídu.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace šifrovacích tříd](configure-cryptography-classes.md)
- [Kryptografické služby](../../standard/security/cryptographic-services.md)
