---
title: Možnost kódování instance
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315618"
---
# <a name="instance-encoding-option"></a>Možnost kódování instance
**Možnost kódování Instance** vlastnost Store Instance pracovního postupu SQL umožňuje určit, zda by měl poskytovatele trvalosti SQL komprimovat informace stavu instance pracovního postupu pomocí algoritmu GZip před uložením informace do databáze trvalosti. Povolené hodnoty této vlastnosti jsou: GZip a None. Výchozí hodnota je žádné. Následující seznam popisuje tyto možnosti.  
  
1. **GZip**. Poskytovatel trvalého kóduje informace o stavu pomocí algoritmu GZip před uložením informace o stavu databáze trvalosti.  
  
2. **Žádný**. Poskytovatel trvalého neprovádí kódování informace o stavu před uložením informace do databáze trvalosti.  
  
 Kódování instance informace o stavu pracovního postupu pomocí GZip snižuje spotřebu paměti ve službě SQL database a také snižuje využití sítě, pokud se databáze nachází na jiný počítač v síti z počítače, na kterém je hostitel služby pracovního postupu spuštění. Obecné pokyny, je nastavit **možnost kódování Instance** vlastnost **žádný** Pokud stav instance pracovního postupu je nízká.
