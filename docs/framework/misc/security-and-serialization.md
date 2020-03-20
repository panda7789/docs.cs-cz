---
title: Zabezpečení a serializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181119"
---
# <a name="security-and-serialization"></a>Zabezpečení a serializace
Vzhledem k tomu, že serializace může umožnit jinému kódu zobrazit nebo upravit data instance <xref:System.Security.Permissions.SecurityPermission> objektu, která by jinak byla nepřístupná, je vyžadováno zvláštní oprávnění kódu provádějícímserializaci: se zadaným příznakem. <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.  
  
 Za normálních okolností jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech pro instanci. Je možné pro kód, který může interpretovat formát k určení, jaké jsou hodnoty dat, nezávisle na usnadnění přístupu člena. Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, opět bez ohledu na pravidla usnadnění.  
  
 Jakýkoli objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být pokud možno neserializovatelný. Pokud musí být serializovatelný, pokuste se, aby určitá pole, která obsahuje citlivá data neserializovatelné. Pokud to nelze provést, uvědomte si, že tato data budou vystavena jakémukoli kódu, který má oprávnění k serializaci, a ujistěte se, že žádné škodlivé kódy mohou získat toto oprávnění.  
  
 Rozhraní <xref:System.Runtime.Serialization.ISerializable> je určeno pouze pro infrastrukturu serializace. Však pokud není chráněn, může potenciálně uvolnit citlivé informace. Pokud zadáte vlastní serializaci implementací **ISerializable**, ujistěte se, že provést následující opatření:  
  
- Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> by měla být explicitně zabezpečena buď požadavkem **SecurityPermission** s **SerializationFormatter** oprávnění zadané nebo ujistěte se, že žádné citlivé informace je uvolněna s výstupem metody. Například:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- Speciální konstruktor používaný pro serializaci by měl také provádět důkladné ověření vstupu a měl by být chráněn nebo soukromý, aby pomohl chránit před zneužitím škodlivým kódem. Měl by vynutit stejné kontroly zabezpečení a oprávnění potřebné k získání instance takové třídy jinými prostředky, jako je například explicitní vytvoření třídy nebo nepřímé vytvoření prostřednictvím nějakého druhu továrny.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
