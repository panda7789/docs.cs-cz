---
title: "Kolekce schématu rozhraní ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="ddb21-102">Kolekce schématu rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="ddb21-102">ODBC Schema Collections</span></span>
<span data-ttu-id="ddb21-103">Tato část popisuje podporu kolekci schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="ddb21-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="ddb21-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="ddb21-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="ddb21-105">Ovladač ODBC Microsoft SQL Server podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="ddb21-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ddb21-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="ddb21-106">Tables</span></span>  
  
-   <span data-ttu-id="ddb21-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="ddb21-107">Indexes</span></span>  
  
-   <span data-ttu-id="ddb21-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-108">Columns</span></span>  
  
-   <span data-ttu-id="ddb21-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-109">Procedures</span></span>  
  
-   <span data-ttu-id="ddb21-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ddb21-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ddb21-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ddb21-112">zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ddb21-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-113">Tables and Views</span></span>  
  
|<span data-ttu-id="ddb21-114">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-114">ColumnName</span></span>|<span data-ttu-id="ddb21-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-116">TABLE_CAT</span></span>|<span data-ttu-id="ddb21-117">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-117">String</span></span>|  
|<span data-ttu-id="ddb21-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-118">TABLE_SCHEM</span></span>|<span data-ttu-id="ddb21-119">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-119">String</span></span>|  
|<span data-ttu-id="ddb21-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-120">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-121">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-121">String</span></span>|  
|<span data-ttu-id="ddb21-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-122">TABLE_TYPE</span></span>|<span data-ttu-id="ddb21-123">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-123">String</span></span>|  
|<span data-ttu-id="ddb21-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-124">REMARKS</span></span>|<span data-ttu-id="ddb21-125">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="ddb21-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="ddb21-126">Indexes</span></span>  
  
|<span data-ttu-id="ddb21-127">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-127">ColumnName</span></span>|<span data-ttu-id="ddb21-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-129">TABLE_CAT</span></span>|<span data-ttu-id="ddb21-130">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-130">String</span></span>|  
|<span data-ttu-id="ddb21-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-131">TABLE_SCHEM</span></span>|<span data-ttu-id="ddb21-132">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-132">String</span></span>|  
|<span data-ttu-id="ddb21-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-133">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-134">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-134">String</span></span>|  
|<span data-ttu-id="ddb21-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ddb21-135">NON_UNIQUE</span></span>|<span data-ttu-id="ddb21-136">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-136">Int16</span></span>|  
|<span data-ttu-id="ddb21-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="ddb21-138">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-138">String</span></span>|  
|<span data-ttu-id="ddb21-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-139">INDEX_NAME</span></span>|<span data-ttu-id="ddb21-140">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-140">String</span></span>|  
|<span data-ttu-id="ddb21-141">TYP</span><span class="sxs-lookup"><span data-stu-id="ddb21-141">TYPE</span></span>|<span data-ttu-id="ddb21-142">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-142">Int16</span></span>|  
|<span data-ttu-id="ddb21-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-144">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-144">Int16</span></span>|  
|<span data-ttu-id="ddb21-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-145">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-146">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-146">String</span></span>|  
|<span data-ttu-id="ddb21-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="ddb21-147">ASC_OR_DESC</span></span>|<span data-ttu-id="ddb21-148">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-148">String</span></span>|  
|<span data-ttu-id="ddb21-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="ddb21-149">CARDINATLITY</span></span>|<span data-ttu-id="ddb21-150">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-150">Int32</span></span>|  
|<span data-ttu-id="ddb21-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-151">PAGES</span></span>|<span data-ttu-id="ddb21-152">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-152">Int32</span></span>|  
|<span data-ttu-id="ddb21-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-153">FILTER_CONDITION</span></span>|<span data-ttu-id="ddb21-154">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-154">String</span></span>|  
|<span data-ttu-id="ddb21-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ddb21-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ddb21-156">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-156">String</span></span>|  
|<span data-ttu-id="ddb21-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-158">Byte</span><span class="sxs-lookup"><span data-stu-id="ddb21-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ddb21-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-159">Columns</span></span>  
  
|<span data-ttu-id="ddb21-160">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-160">ColumnName</span></span>|<span data-ttu-id="ddb21-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-162">TABLE_CAT</span></span>|<span data-ttu-id="ddb21-163">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-163">String</span></span>|  
|<span data-ttu-id="ddb21-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-164">TABLE_SCHEM</span></span>|<span data-ttu-id="ddb21-165">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-165">String</span></span>|  
|<span data-ttu-id="ddb21-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-166">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-167">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-167">String</span></span>|  
|<span data-ttu-id="ddb21-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-168">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-169">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-169">String</span></span>|  
|<span data-ttu-id="ddb21-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-170">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-171">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-171">Int16</span></span>|  
|<span data-ttu-id="ddb21-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-172">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-173">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-173">String</span></span>|  
|<span data-ttu-id="ddb21-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ddb21-174">COLUMN_SIZE</span></span>|<span data-ttu-id="ddb21-175">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-175">Int32</span></span>|  
|<span data-ttu-id="ddb21-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="ddb21-177">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-177">Int32</span></span>|  
|<span data-ttu-id="ddb21-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ddb21-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ddb21-179">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-179">Int16</span></span>|  
|<span data-ttu-id="ddb21-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ddb21-181">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-181">Int16</span></span>|  
|<span data-ttu-id="ddb21-182">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-182">NULLABLE</span></span>|<span data-ttu-id="ddb21-183">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-183">Int16</span></span>|  
|<span data-ttu-id="ddb21-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-184">REMARKS</span></span>|<span data-ttu-id="ddb21-185">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-185">String</span></span>|  
|<span data-ttu-id="ddb21-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ddb21-186">COLUMN_DEF</span></span>|<span data-ttu-id="ddb21-187">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-187">String</span></span>|  
|<span data-ttu-id="ddb21-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-189">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-189">Int16</span></span>|  
|<span data-ttu-id="ddb21-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ddb21-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ddb21-191">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-191">Int16</span></span>|  
|<span data-ttu-id="ddb21-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ddb21-193">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-193">Int32</span></span>|  
|<span data-ttu-id="ddb21-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-195">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-195">Int32</span></span>|  
|<span data-ttu-id="ddb21-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ddb21-196">IS_NULLABLE</span></span>|<span data-ttu-id="ddb21-197">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-197">String</span></span>|  
|<span data-ttu-id="ddb21-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ddb21-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ddb21-199">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-199">String</span></span>|  
|<span data-ttu-id="ddb21-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ddb21-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ddb21-201">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-201">String</span></span>|  
|<span data-ttu-id="ddb21-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-203">Byte</span><span class="sxs-lookup"><span data-stu-id="ddb21-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ddb21-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-204">Procedures</span></span>  
  
|<span data-ttu-id="ddb21-205">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-205">ColumnName</span></span>|<span data-ttu-id="ddb21-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="ddb21-208">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-208">String</span></span>|  
|<span data-ttu-id="ddb21-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ddb21-210">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-210">String</span></span>|  
|<span data-ttu-id="ddb21-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-212">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-212">String</span></span>|  
|<span data-ttu-id="ddb21-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-214">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-214">Int32</span></span>|  
|<span data-ttu-id="ddb21-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-216">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-216">Int32</span></span>|  
|<span data-ttu-id="ddb21-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ddb21-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ddb21-218">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-218">Int32</span></span>|  
|<span data-ttu-id="ddb21-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-219">REMARKS</span></span>|<span data-ttu-id="ddb21-220">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-220">String</span></span>|  
|<span data-ttu-id="ddb21-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ddb21-222">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ddb21-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ddb21-224">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-224">ColumnName</span></span>|<span data-ttu-id="ddb21-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="ddb21-227">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-227">String</span></span>|  
|<span data-ttu-id="ddb21-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ddb21-229">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-229">String</span></span>|  
|<span data-ttu-id="ddb21-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-231">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-231">String</span></span>|  
|<span data-ttu-id="ddb21-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-232">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-233">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-233">String</span></span>|  
|<span data-ttu-id="ddb21-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-234">COLUMN_TYPE</span></span>|<span data-ttu-id="ddb21-235">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-235">Int16</span></span>|  
|<span data-ttu-id="ddb21-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-236">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-237">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-237">Int16</span></span>|  
|<span data-ttu-id="ddb21-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-238">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-239">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-239">String</span></span>|  
|<span data-ttu-id="ddb21-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ddb21-240">COLUMN_SIZE</span></span>|<span data-ttu-id="ddb21-241">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-241">Int32</span></span>|  
|<span data-ttu-id="ddb21-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="ddb21-243">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-243">Int32</span></span>|  
|<span data-ttu-id="ddb21-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ddb21-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ddb21-245">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-245">Int16</span></span>|  
|<span data-ttu-id="ddb21-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ddb21-247">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-247">Int16</span></span>|  
|<span data-ttu-id="ddb21-248">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-248">NULLABLE</span></span>|<span data-ttu-id="ddb21-249">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-249">Int16</span></span>|  
|<span data-ttu-id="ddb21-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-250">REMARKS</span></span>|<span data-ttu-id="ddb21-251">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-251">String</span></span>|  
|<span data-ttu-id="ddb21-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ddb21-252">COLUMN_DEF</span></span>|<span data-ttu-id="ddb21-253">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-253">String</span></span>|  
|<span data-ttu-id="ddb21-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-255">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-255">Int16</span></span>|  
|<span data-ttu-id="ddb21-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ddb21-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ddb21-257">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-257">Int16</span></span>|  
|<span data-ttu-id="ddb21-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ddb21-259">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-259">Int32</span></span>|  
|<span data-ttu-id="ddb21-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-261">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-261">Int32</span></span>|  
|<span data-ttu-id="ddb21-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ddb21-262">IS_NULLABLE</span></span>|<span data-ttu-id="ddb21-263">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-263">String</span></span>|  
|<span data-ttu-id="ddb21-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ddb21-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ddb21-265">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-265">String</span></span>|  
|<span data-ttu-id="ddb21-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ddb21-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ddb21-267">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-267">String</span></span>|  
|<span data-ttu-id="ddb21-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-269">Byte</span><span class="sxs-lookup"><span data-stu-id="ddb21-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="ddb21-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ddb21-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="ddb21-271">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-271">ColumnName</span></span>|<span data-ttu-id="ddb21-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="ddb21-274">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-274">String</span></span>|  
|<span data-ttu-id="ddb21-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ddb21-276">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-276">String</span></span>|  
|<span data-ttu-id="ddb21-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-278">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-278">String</span></span>|  
|<span data-ttu-id="ddb21-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-279">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-280">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-280">String</span></span>|  
|<span data-ttu-id="ddb21-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-281">COLUMN_TYPE</span></span>|<span data-ttu-id="ddb21-282">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-282">Int16</span></span>|  
|<span data-ttu-id="ddb21-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-283">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-284">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-284">Int16</span></span>|  
|<span data-ttu-id="ddb21-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-285">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-286">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-286">String</span></span>|  
|<span data-ttu-id="ddb21-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ddb21-287">COLUMN_SIZE</span></span>|<span data-ttu-id="ddb21-288">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-288">Int32</span></span>|  
|<span data-ttu-id="ddb21-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="ddb21-290">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-290">Int32</span></span>|  
|<span data-ttu-id="ddb21-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ddb21-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ddb21-292">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-292">Int16</span></span>|  
|<span data-ttu-id="ddb21-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ddb21-294">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-294">Int16</span></span>|  
|<span data-ttu-id="ddb21-295">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-295">NULLABLE</span></span>|<span data-ttu-id="ddb21-296">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-296">Int16</span></span>|  
|<span data-ttu-id="ddb21-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-297">REMARKS</span></span>|<span data-ttu-id="ddb21-298">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-298">String</span></span>|  
|<span data-ttu-id="ddb21-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ddb21-299">COLUMN_DEF</span></span>|<span data-ttu-id="ddb21-300">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-300">String</span></span>|  
|<span data-ttu-id="ddb21-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-302">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-302">Int16</span></span>|  
|<span data-ttu-id="ddb21-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ddb21-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ddb21-304">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-304">Int16</span></span>|  
|<span data-ttu-id="ddb21-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ddb21-306">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-306">Int32</span></span>|  
|<span data-ttu-id="ddb21-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-308">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-308">Int32</span></span>|  
|<span data-ttu-id="ddb21-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ddb21-309">IS_NULLABLE</span></span>|<span data-ttu-id="ddb21-310">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-310">String</span></span>|  
|<span data-ttu-id="ddb21-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ddb21-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ddb21-312">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-312">String</span></span>|  
|<span data-ttu-id="ddb21-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ddb21-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ddb21-314">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-314">String</span></span>|  
|<span data-ttu-id="ddb21-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-316">Byte</span><span class="sxs-lookup"><span data-stu-id="ddb21-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="ddb21-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="ddb21-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="ddb21-318">Ovladač ODBC Microsoft SQL Server Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="ddb21-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ddb21-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="ddb21-319">Tables</span></span>  
  
-   <span data-ttu-id="ddb21-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-320">Columns</span></span>  
  
-   <span data-ttu-id="ddb21-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-321">Procedures</span></span>  
  
-   <span data-ttu-id="ddb21-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ddb21-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ddb21-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ddb21-324">zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-324">Views</span></span>  
  
-   <span data-ttu-id="ddb21-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="ddb21-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ddb21-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-326">Tables and Views</span></span>  
  
|<span data-ttu-id="ddb21-327">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-327">ColumnName</span></span>|<span data-ttu-id="ddb21-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-330">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-330">String</span></span>|  
|<span data-ttu-id="ddb21-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-331">TABLE_OWNER</span></span>|<span data-ttu-id="ddb21-332">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-332">String</span></span>|  
|<span data-ttu-id="ddb21-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-333">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-334">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-334">String</span></span>|  
|<span data-ttu-id="ddb21-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-335">TABLE_TYPE</span></span>|<span data-ttu-id="ddb21-336">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-336">String</span></span>|  
|<span data-ttu-id="ddb21-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-337">REMARKS</span></span>|<span data-ttu-id="ddb21-338">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ddb21-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-339">Columns</span></span>  
  
|<span data-ttu-id="ddb21-340">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-340">ColumnName</span></span>|<span data-ttu-id="ddb21-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-343">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-343">String</span></span>|  
|<span data-ttu-id="ddb21-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-344">TABLE_OWNER</span></span>|<span data-ttu-id="ddb21-345">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-345">String</span></span>|  
|<span data-ttu-id="ddb21-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-346">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-347">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-347">String</span></span>|  
|<span data-ttu-id="ddb21-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-348">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-349">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-349">String</span></span>|  
|<span data-ttu-id="ddb21-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-350">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-351">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-351">Int16</span></span>|  
|<span data-ttu-id="ddb21-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-352">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-353">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-353">String</span></span>|  
|<span data-ttu-id="ddb21-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="ddb21-354">PRECISION</span></span>|<span data-ttu-id="ddb21-355">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-355">Int32</span></span>|  
|<span data-ttu-id="ddb21-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="ddb21-356">LENGTH</span></span>|<span data-ttu-id="ddb21-357">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-357">Int32</span></span>|  
|<span data-ttu-id="ddb21-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-358">SCALE</span></span>|<span data-ttu-id="ddb21-359">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-359">Int16</span></span>|  
|<span data-ttu-id="ddb21-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-360">RADIX</span></span>|<span data-ttu-id="ddb21-361">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-361">Int16</span></span>|  
|<span data-ttu-id="ddb21-362">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-362">NULLABLE</span></span>|<span data-ttu-id="ddb21-363">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-363">Int16</span></span>|  
|<span data-ttu-id="ddb21-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-364">REMARKS</span></span>|<span data-ttu-id="ddb21-365">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-365">String</span></span>|  
|<span data-ttu-id="ddb21-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-367">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ddb21-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-368">Procedures</span></span>  
  
|<span data-ttu-id="ddb21-369">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-369">ColumnName</span></span>|<span data-ttu-id="ddb21-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-372">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-372">String</span></span>|  
|<span data-ttu-id="ddb21-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ddb21-374">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-374">String</span></span>|  
|<span data-ttu-id="ddb21-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-376">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-376">String</span></span>|  
|<span data-ttu-id="ddb21-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-378">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-378">Int16</span></span>|  
|<span data-ttu-id="ddb21-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-380">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-380">Int16</span></span>|  
|<span data-ttu-id="ddb21-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ddb21-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ddb21-382">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-382">Int16</span></span>|  
|<span data-ttu-id="ddb21-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-383">REMARKS</span></span>|<span data-ttu-id="ddb21-384">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-384">String</span></span>|  
|<span data-ttu-id="ddb21-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ddb21-386">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ddb21-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ddb21-388">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-388">ColumnName</span></span>|<span data-ttu-id="ddb21-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-391">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-391">String</span></span>|  
|<span data-ttu-id="ddb21-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ddb21-393">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-393">String</span></span>|  
|<span data-ttu-id="ddb21-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-395">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-395">String</span></span>|  
|<span data-ttu-id="ddb21-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-396">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-397">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-397">String</span></span>|  
|<span data-ttu-id="ddb21-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-398">COLUMN_TYPE</span></span>|<span data-ttu-id="ddb21-399">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-399">Int16</span></span>|  
|<span data-ttu-id="ddb21-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-400">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-401">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-401">Int16</span></span>|  
|<span data-ttu-id="ddb21-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-402">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-403">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-403">String</span></span>|  
|<span data-ttu-id="ddb21-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="ddb21-404">PRECISION</span></span>|<span data-ttu-id="ddb21-405">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-405">Int32</span></span>|  
|<span data-ttu-id="ddb21-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="ddb21-406">LENGTH</span></span>|<span data-ttu-id="ddb21-407">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-407">Int32</span></span>|  
|<span data-ttu-id="ddb21-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-408">SCALE</span></span>|<span data-ttu-id="ddb21-409">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-409">Int16</span></span>|  
|<span data-ttu-id="ddb21-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-410">RADIX</span></span>|<span data-ttu-id="ddb21-411">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-411">Int16</span></span>|  
|<span data-ttu-id="ddb21-412">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-412">NULLABLE</span></span>|<span data-ttu-id="ddb21-413">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-413">Int16</span></span>|  
|<span data-ttu-id="ddb21-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-414">REMARKS</span></span>|<span data-ttu-id="ddb21-415">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-415">String</span></span>|  
|<span data-ttu-id="ddb21-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-416">OVERLOAD</span></span>|<span data-ttu-id="ddb21-417">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-417">Int32</span></span>|  
|<span data-ttu-id="ddb21-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-419">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="ddb21-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="ddb21-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="ddb21-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="ddb21-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ddb21-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="ddb21-422">Tables</span></span>  
  
-   <span data-ttu-id="ddb21-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="ddb21-423">Indexes</span></span>  
  
-   <span data-ttu-id="ddb21-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-424">Columns</span></span>  
  
-   <span data-ttu-id="ddb21-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-425">Procedures</span></span>  
  
-   <span data-ttu-id="ddb21-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ddb21-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ddb21-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ddb21-428">zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="ddb21-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="ddb21-429">Tables and Views</span></span>  
  
|<span data-ttu-id="ddb21-430">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-430">ColumnName</span></span>|<span data-ttu-id="ddb21-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-433">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-433">String</span></span>|  
|<span data-ttu-id="ddb21-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-434">TABLE_OWNER</span></span>|<span data-ttu-id="ddb21-435">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-435">String</span></span>|  
|<span data-ttu-id="ddb21-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-436">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-437">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-437">String</span></span>|  
|<span data-ttu-id="ddb21-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-438">TABLE_TYPE</span></span>|<span data-ttu-id="ddb21-439">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-439">String</span></span>|  
|<span data-ttu-id="ddb21-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-440">REMARKS</span></span>|<span data-ttu-id="ddb21-441">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ddb21-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="ddb21-442">Columns</span></span>  
  
|<span data-ttu-id="ddb21-443">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-443">ColumnName</span></span>|<span data-ttu-id="ddb21-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-446">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-446">String</span></span>|  
|<span data-ttu-id="ddb21-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-447">TABLE_OWNER</span></span>|<span data-ttu-id="ddb21-448">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-448">String</span></span>|  
|<span data-ttu-id="ddb21-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-449">TABLE_NAME</span></span>|<span data-ttu-id="ddb21-450">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-450">String</span></span>|  
|<span data-ttu-id="ddb21-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-451">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-452">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-452">String</span></span>|  
|<span data-ttu-id="ddb21-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-453">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-454">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-454">Int16</span></span>|  
|<span data-ttu-id="ddb21-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-455">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-456">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-456">String</span></span>|  
|<span data-ttu-id="ddb21-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="ddb21-457">PRECISION</span></span>|<span data-ttu-id="ddb21-458">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-458">Int32</span></span>|  
|<span data-ttu-id="ddb21-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="ddb21-459">LENGTH</span></span>|<span data-ttu-id="ddb21-460">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-460">Int32</span></span>|  
|<span data-ttu-id="ddb21-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-461">SCALE</span></span>|<span data-ttu-id="ddb21-462">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-462">Int16</span></span>|  
|<span data-ttu-id="ddb21-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-463">RADIX</span></span>|<span data-ttu-id="ddb21-464">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-464">Int16</span></span>|  
|<span data-ttu-id="ddb21-465">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-465">NULLABLE</span></span>|<span data-ttu-id="ddb21-466">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-466">Int16</span></span>|  
|<span data-ttu-id="ddb21-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-467">REMARKS</span></span>|<span data-ttu-id="ddb21-468">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-468">String</span></span>|  
|<span data-ttu-id="ddb21-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-470">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ddb21-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="ddb21-471">Procedures</span></span>  
  
|<span data-ttu-id="ddb21-472">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-472">ColumnName</span></span>|<span data-ttu-id="ddb21-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-475">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-475">String</span></span>|  
|<span data-ttu-id="ddb21-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ddb21-477">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-477">String</span></span>|  
|<span data-ttu-id="ddb21-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-479">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-479">String</span></span>|  
|<span data-ttu-id="ddb21-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-481">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-481">Int16</span></span>|  
|<span data-ttu-id="ddb21-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ddb21-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ddb21-483">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-483">Int16</span></span>|  
|<span data-ttu-id="ddb21-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ddb21-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ddb21-485">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-485">Int16</span></span>|  
|<span data-ttu-id="ddb21-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-486">REMARKS</span></span>|<span data-ttu-id="ddb21-487">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-487">String</span></span>|  
|<span data-ttu-id="ddb21-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ddb21-489">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ddb21-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ddb21-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ddb21-491">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-491">ColumnName</span></span>|<span data-ttu-id="ddb21-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ddb21-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ddb21-494">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-494">String</span></span>|  
|<span data-ttu-id="ddb21-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddb21-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ddb21-496">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-496">String</span></span>|  
|<span data-ttu-id="ddb21-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-498">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-498">String</span></span>|  
|<span data-ttu-id="ddb21-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-499">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-500">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-500">String</span></span>|  
|<span data-ttu-id="ddb21-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-501">COLUMN_TYPE</span></span>|<span data-ttu-id="ddb21-502">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-502">Int16</span></span>|  
|<span data-ttu-id="ddb21-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-503">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-504">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-504">Int16</span></span>|  
|<span data-ttu-id="ddb21-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-505">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-506">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-506">String</span></span>|  
|<span data-ttu-id="ddb21-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="ddb21-507">PRECISION</span></span>|<span data-ttu-id="ddb21-508">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-508">Int32</span></span>|  
|<span data-ttu-id="ddb21-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="ddb21-509">LENGTH</span></span>|<span data-ttu-id="ddb21-510">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-510">Int32</span></span>|  
|<span data-ttu-id="ddb21-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-511">SCALE</span></span>|<span data-ttu-id="ddb21-512">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-512">Int16</span></span>|  
|<span data-ttu-id="ddb21-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-513">RADIX</span></span>|<span data-ttu-id="ddb21-514">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-514">Int16</span></span>|  
|<span data-ttu-id="ddb21-515">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-515">NULLABLE</span></span>|<span data-ttu-id="ddb21-516">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-516">Int16</span></span>|  
|<span data-ttu-id="ddb21-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-517">REMARKS</span></span>|<span data-ttu-id="ddb21-518">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-518">String</span></span>|  
|<span data-ttu-id="ddb21-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="ddb21-519">OVERLOAD</span></span>|<span data-ttu-id="ddb21-520">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-520">Int32</span></span>|  
|<span data-ttu-id="ddb21-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-522">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="ddb21-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ddb21-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="ddb21-524">columnName</span><span class="sxs-lookup"><span data-stu-id="ddb21-524">ColumnName</span></span>|<span data-ttu-id="ddb21-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ddb21-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ddb21-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ddb21-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="ddb21-527">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-527">String</span></span>|  
|<span data-ttu-id="ddb21-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ddb21-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ddb21-529">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-529">String</span></span>|  
|<span data-ttu-id="ddb21-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="ddb21-531">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-531">String</span></span>|  
|<span data-ttu-id="ddb21-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-532">COLUMN_NAME</span></span>|<span data-ttu-id="ddb21-533">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-533">String</span></span>|  
|<span data-ttu-id="ddb21-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-534">COLUMN_TYPE</span></span>|<span data-ttu-id="ddb21-535">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-535">Int16</span></span>|  
|<span data-ttu-id="ddb21-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-536">DATA_TYPE</span></span>|<span data-ttu-id="ddb21-537">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-537">Int16</span></span>|  
|<span data-ttu-id="ddb21-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ddb21-538">TYPE_NAME</span></span>|<span data-ttu-id="ddb21-539">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-539">String</span></span>|  
|<span data-ttu-id="ddb21-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ddb21-540">COLUMN_SIZE</span></span>|<span data-ttu-id="ddb21-541">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-541">Int32</span></span>|  
|<span data-ttu-id="ddb21-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="ddb21-543">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-543">Int32</span></span>|  
|<span data-ttu-id="ddb21-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ddb21-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ddb21-545">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-545">Int16</span></span>|  
|<span data-ttu-id="ddb21-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ddb21-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ddb21-547">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-547">Int16</span></span>|  
|<span data-ttu-id="ddb21-548">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="ddb21-548">NULLABLE</span></span>|<span data-ttu-id="ddb21-549">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-549">Int16</span></span>|  
|<span data-ttu-id="ddb21-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="ddb21-550">REMARKS</span></span>|<span data-ttu-id="ddb21-551">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-551">String</span></span>|  
|<span data-ttu-id="ddb21-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ddb21-552">COLUMN_DEF</span></span>|<span data-ttu-id="ddb21-553">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-553">String</span></span>|  
|<span data-ttu-id="ddb21-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ddb21-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ddb21-555">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-555">Int16</span></span>|  
|<span data-ttu-id="ddb21-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ddb21-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ddb21-557">Int16</span><span class="sxs-lookup"><span data-stu-id="ddb21-557">Int16</span></span>|  
|<span data-ttu-id="ddb21-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ddb21-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ddb21-559">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-559">Int32</span></span>|  
|<span data-ttu-id="ddb21-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ddb21-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="ddb21-561">Int32</span><span class="sxs-lookup"><span data-stu-id="ddb21-561">Int32</span></span>|  
|<span data-ttu-id="ddb21-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ddb21-562">IS_NULLABLE</span></span>|<span data-ttu-id="ddb21-563">String</span><span class="sxs-lookup"><span data-stu-id="ddb21-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddb21-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddb21-564">See Also</span></span>  
 [<span data-ttu-id="ddb21-565">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ddb21-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
