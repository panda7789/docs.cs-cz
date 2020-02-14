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
ms.openlocfilehash: cb0ba120eeb57788c0525d45b714ad8edd2c39ed
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216967"
---
# <a name="security-and-serialization"></a>Zabezpečení a serializace
Vzhledem k tomu, že serializace může ostatním kód dovolit zobrazit nebo upravit data instance objektů, která by jinak nebyla přístupná, je vyžadováno zvláštní oprávnění pro provádění serializace kódu: <xref:System.Security.Permissions.SecurityPermission> se zadaným příznakem <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>. Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.  
  
 Obvykle jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech instance. Je možné, že kód, který může interpretovat formát pro určení hodnot dat, nezávisle na přístupnost člena. Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, a to bez ohledu na pravidla přístupnosti.  
  
 Libovolný objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být, pokud je to možné, neserializovatelné. Pokud musí být serializovatelný, zkuste nastavit konkrétní pole, která uchovávají citlivá data neserializovatelné. Pokud to není možné, mějte na paměti, že tato data budou vystavena kódu, který má oprávnění k serializaci, a ujistěte se, že žádný škodlivý kód nemůže získat toto oprávnění.  
  
 Rozhraní <xref:System.Runtime.Serialization.ISerializable> je určeno pro použití pouze infrastrukturou serializace. Pokud je ale nechráněný, může potenciálně vydávat citlivé informace. Pokud zadáte vlastní serializaci implementující rozhraní **ISerializable**, ujistěte se, že jste provedli následující opatření:  
  
- Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> by měla být explicitně zabezpečena buď **tak, že vyžaduje, aby** došlo k **SerializationFormatter** oprávnění, nebo zajistěte, aby s výstupem metody nebyly zveřejněny žádné citlivé informace. Například:  
  
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
  
- Speciální konstruktor, který se používá pro serializaci, by měl také provádět důkladné ověření vstupu a měl by být chráněný nebo soukromý, aby bylo možné chránit před zneužitím škodlivý kód. Měla by vyhovět stejným kontrolám zabezpečení a oprávněním, která jsou nutná k získání instance této třídy jakýmkoli jiným způsobem, například explicitním vytvořením třídy nebo jejím přímým vytvořením pomocí nějakého typu objektu pro vytváření.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
