---
title: 'Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a183f81a73c3c8034d9ba7366be8b36d425263da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="8bfad-102">Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;</span><span class="sxs-lookup"><span data-stu-id="8bfad-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="8bfad-103">Došlo k potížím, vytvoření souboru.</span><span class="sxs-lookup"><span data-stu-id="8bfad-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="8bfad-104">Výstupní soubor nelze otevřít pro zápis.</span><span class="sxs-lookup"><span data-stu-id="8bfad-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="8bfad-105">Soubor (nebo ve složce obsahující soubor) můžou být otevřené pro výhradní použití jiný proces, nebo může mít jeho nastaven atribut jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8bfad-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="8bfad-106">Běžné situace, kdy je výhradně otevřen souboru jsou:</span><span class="sxs-lookup"><span data-stu-id="8bfad-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="8bfad-107">Aplikace je již spuštěna a pomocí jeho soubory.</span><span class="sxs-lookup"><span data-stu-id="8bfad-107">The application is already running and using its files.</span></span> <span data-ttu-id="8bfad-108">Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="8bfad-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="8bfad-109">Jiná aplikace má otevřít soubor.</span><span class="sxs-lookup"><span data-stu-id="8bfad-109">Another application has opened the file.</span></span> <span data-ttu-id="8bfad-110">Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace, je přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="8bfad-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="8bfad-111">Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.</span><span class="sxs-lookup"><span data-stu-id="8bfad-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="8bfad-112">Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8bfad-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="8bfad-113">**ID chyby:** BC31019</span><span class="sxs-lookup"><span data-stu-id="8bfad-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8bfad-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8bfad-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="8bfad-115">Kompilace programu zjistíte, pokud se chyba objeví znovu.</span><span class="sxs-lookup"><span data-stu-id="8bfad-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="8bfad-116">Pokud potíže potrvají, uložte si práci a restartujte [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8bfad-116">If the error continues, save your work and restart [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
3.  <span data-ttu-id="8bfad-117">Pokud potíže potrvají, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="8bfad-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="8bfad-118">Pokud se chyba objeví znovu, přeinstalujte jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bfad-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="8bfad-119">Pokud chyba přetrvává i po přeinstalování, upozorněte služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="8bfad-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="8bfad-120">Chcete-li zkontrolovat atributů souboru v Průzkumníkovi souborů</span><span class="sxs-lookup"><span data-stu-id="8bfad-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="8bfad-121">Otevřete složku, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="8bfad-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="8bfad-122">Klikněte **zobrazení** ikonu a vyberte **podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="8bfad-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="8bfad-123">Klikněte pravým tlačítkem myši na záhlaví sloupce a vyberte **atributy** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="8bfad-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="8bfad-124">Chcete-li změnit atributy souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="8bfad-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="8bfad-125">V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8bfad-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="8bfad-126">V **atributy** části **Obecné** zrušte **jen pro čtení** pole.</span><span class="sxs-lookup"><span data-stu-id="8bfad-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="8bfad-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="8bfad-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bfad-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bfad-128">See Also</span></span>  
 [<span data-ttu-id="8bfad-129">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="8bfad-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
