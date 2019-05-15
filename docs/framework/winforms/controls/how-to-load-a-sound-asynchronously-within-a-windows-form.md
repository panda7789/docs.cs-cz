---
title: 'Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 5f533d82fcca07a2b64bdbbfb160a7b2a23ce540
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592372"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms
Následující příklad kódu asynchronně načte zvuk z adresy URL a pak hraje v novém vláknu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému a System.Windows.Forms.  
  
- Nahradit název souboru `"http://www.tailspintoys.com/sounds/stop.wav"` s platným názvem souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Operace se soubory by měl být uzavřen v rámci příslušné zpracování výjimek bloků.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název cesty je poškozený. Například obsahuje znaky, které nejsou platné nebo je prázdné znaky (<xref:System.ArgumentException> třídy).  
  
- Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
- Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).  
  
- Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
- Cesta není platná (<xref:System.IO.DirectoryNotFoundException> třídy).  
  
- Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [Postupy: Přehrávání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
