---
title: "Cílení na rozhraní .NET Framework 2.0 v systému Windows 8"
description: "Informace o cílení na starší verzi rozhraní .NET Framework, při použití F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a>Cílení na starší verze rozhraní .NET

> [!NOTE]
V tomto článku není aktuální pomocí nejnovější sady Visual Studio.  Bude aktualizována.

Může objevit následující chyba, pokud se pokusíte rozhraní .NET Framework 2.0, 3.0 nebo 3.5 v F # projektu při instalaci sady Visual Studio na Windows 8.1: 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

Tato chyba se označuje dojde za následující kombinace podmínky:


- Visual Studio nainstalujete na Windows 8.1.
<br />

- Před instalací sady Visual Studio je nebyla povolit rozhraní .NET Framework 3.5.
<br />

- Cílem vašeho projektu je .NET Framework 2.0, 3.0 nebo 3.5.
<br />

Při instalaci sady Visual Studio, zjistí nainstalovaných verzí rozhraní .NET Framework a pouze v případě, že rozhraní .NET Framework 3.5 je nainstalované a povolené nainstaluje 2.0 Runtime F #.


## <a name="resolving-the-error"></a>Řešení chyby
Chcete-li tuto chybu vyřešit, můžete buď cílový novější verzi rozhraní .NET Framework, nebo můžete povolit rozhraní .NET Framework 3.5 ve Windows 8.1 a pak nainstalovat modul runtime F # 2.0 spuštěním instalačního programu pro sadu Visual Studio s **Repair** možnost.


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Chcete-li povolit rozhraní .NET Framework 3.5 ve Windows 8.1

1. Na **spustit** obrazovky, začnete-li zadat **ovládací panely**.
<br />  Jako zadáte název, **ovládací panely** ikonu se zobrazí pod **aplikace** záhlaví.
<br />

2. Vyberte **ovládací panely** ikonu, vyberte **programy** ikonu a potom zvolte **Windows zapnout nebo vypnout funkce** odkaz.
<br />

3. Ujistěte se, že **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtávací políčko je zaškrtnuto a potom vyberte **OK** tlačítko.
<br />  Nemusíte zaškrtněte políčka pro všechny podřízené uzly pro volitelné součásti rozhraní .NET Framework.
<br />  Rozhraní .NET Framework 3.5 je povoleno, pokud ji už nebyl.
<br />


#### <a name="to-install-the-f-20-runtime"></a>Chcete-li nainstalovat modul runtime F # 2.0

1. V Ovládacích panelech, vyberte **programy** propojit a potom zvolte **programy a funkce** odkaz.
<br />

2. V seznamu nainstalovaných programů, vyberte edice sady Visual Studio, který jste nainstalovali a potom zvolte **změnu** tlačítko.
<br />

3. Po spuštění instalace, klikněte **Repair** tlačítko.
<br />  Další informace najdete v tématu [instalaci sady Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).
<br />
## <a name="see-also"></a>Viz také
[Visual F #](../index.md)
