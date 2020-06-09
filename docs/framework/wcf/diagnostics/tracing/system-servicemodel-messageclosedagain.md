---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580434"
---
# <a name="systemservicemodelmessageclosedagain"></a>System.ServiceModel.MessageClosedAgain
System.ServiceModel.MessageClosedAgain  
  
## <a name="description"></a>Popis  
 Zpráva byla znovu zavřena.  
  
 Zpráva by měla být zavřena pouze jednou. Pokud je toto trasování generováno v uživatelském rozšíření kódu, znamená to, že kód rozšíření uživatele zavírá zprávu, která již byla zavřena. Pokud se toto trasování generuje prostřednictvím kódu produktu, znamená to, že kód rozšíření uživatele může potenciálně zavřít zprávu příliš brzy.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
