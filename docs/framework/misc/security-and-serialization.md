---
title: Zabezpečení a serializace
description: Přečtěte si o zabezpečení a serializaci. Pomocí SecurityPermission se zadaným příznakem SerializationFormatter můžete zobrazit nebo upravit data instance objektu.
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
ms.openlocfilehash: f19641ad2154631b4eab5104252c12b73b9084fd
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309271"
---
# <a name="security-and-serialization"></a>Zabezpečení a serializace

Vzhledem k tomu, že serializace může ostatním kód dovolit zobrazit nebo upravit data instance objektů, která by jinak nebyla přístupná, je pro provádění serializace kódu vyžadováno speciální oprávnění: <xref:System.Security.Permissions.SecurityPermission> se <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> zadaným příznakem. Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.  
  
 Obvykle jsou všechna pole instance objektu serializována, což znamená, že data jsou reprezentována v serializovaných datech instance. Je možné, že kód, který může interpretovat formát pro určení hodnot dat, nezávisle na přístupnost člena. Podobně deserializace extrahuje data z serializované reprezentace a nastaví stav objektu přímo, a to bez ohledu na pravidla přístupnosti.  
  
 Libovolný objekt, který by mohl obsahovat data citlivá na zabezpečení, by měl být, pokud je to možné, neserializovatelné. Pokud musí být serializovatelný, zkuste nastavit konkrétní pole, která uchovávají citlivá data neserializovatelné. Pokud tato pole nelze nastavit jako neserializovatelné, budou citlivá data vystavena jakémukoli kódu, který má oprávnění k serializaci. Ujistěte se, že toto oprávnění nelze získat bez škodlivého kódu.  
  
 <xref:System.Runtime.Serialization.ISerializable>Rozhraní je určeno pro použití pouze infrastrukturou serializace. Pokud je ale nechráněný, může potenciálně vydávat citlivé informace. Pokud zadáte vlastní serializaci implementující rozhraní **ISerializable**, ujistěte se, že jste provedli následující opatření:  
  
- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>Metoda by měla být explicitně zabezpečena tím, že **SecurityPermission** vyžaduje, aby došlo k zadání **SerializationFormatter** oprávnění, nebo aby se zajistilo, že nejsou uvolněny žádné citlivé informace s výstupem metody. Příklad:  
  
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
