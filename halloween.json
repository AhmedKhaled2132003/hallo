// ==UserScript==
// @name         Halloween Event ENC - Mod by Ahmed Khaled
// @namespace    https://www.facebook.com/Dr.Ahmed.FamilyFarm/
// @version      1.0
// @description  إنهاء تلقائى لطلبات مهمة الهالوين فى حالة وجود المطلوب بالحظيرة - يعمل بجميع نسخ اللعبة
// @author       أحمد خالد
// @match        *.centurygames.com/*
// @icon         https://www.google.com/s2/favicons?sz=64&domain=centurygames.com
// @grant        unsafeWindow
// @run-at       document-end
// ==/UserScript==

(async function () {
  'use strict';

  function waitForGameReady() {
    return new Promise((resolve) => {
      const check = setInterval(() => {
        if (
          unsafeWindow?.micro?.NetManager &&
          unsafeWindow?.NetUtils &&
          unsafeWindow?.GF?.loginModel
        ) {
          clearInterval(check);
          resolve();
        }
      }, 500);
    });
  }

  function disableProtection() {
    try {
      unsafeWindow.micro.NetManager.prototype.isAmfOk = function () {
        return true;
      };
      unsafeWindow.micro.NetManager.prototype.getErrorMsg = function () {
        return true;
      };
      console.log('✅ تم تعطيل حماية الأحداث');
    } catch (e) {
      console.warn('❌ فشل في تعطيل الحماية:', e);
    }
  }

  await waitForGameReady();
  disableProtection();

  const menu = document.createElement('button');
  menu.innerText = 'أحمد خالد';
  menu.onclick = async function () {
    const confirmStart = confirm('التشغيل التلقائى لإنهاء طلبات مهمة وقت مرح مع رجل الثلج\nتأكيد العملية؟');
    if (!confirmStart) return;

    const infoBox = document.createElement('div');
    infoBox.innerText = 'جارٍ إنهاء الطلبات تلقائياً - برمجة: أحمد خالد';
    infoBox.style.cssText = `
      position: fixed;
      top: 45px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0, 0, 0, 0.4);
      border: 1px solid #aaa;
      border-radius: 6px;
      padding: 4px 10px;
      font-size: 12px;
      color: white;
      font-weight: bold;
      z-index: 9999;
      font-family: Arial;
    `;
    document.body.appendChild(infoBox);

    const net = unsafeWindow.NetUtils;
    const request = async (action, wid) => {
      return net.request('/Activity/HalloweenEvent', { action, wid });
    };

    while (true) {
      const points = unsafeWindow.GF.loginModel.getGiftsNumById(244884);
      infoBox.innerText = `جارٍ إنهاء الطلبات تلقائياً - لديك ⚪ ${points} نقطة - برمجة: أحمد خالد`;

      await request('openWindow', 1);
      await request('refreshWindow', 1);
      await request('closeWindow', 1);

      await request('openWindow', 2);
      await request('refreshWindow', 2);
      await request('closeWindow', 2);

      await request('openWindow', 3);
      await request('refreshWindow', 3);
      await request('closeWindow', 3);

      await request('openWindow', 4);
      await request('refreshWindow', 4);
      await request('closeWindow', 4);

      await request('openWindow', 5);
      await request('refreshWindow', 5);
      await request('closeWindow', 5);
      await new Promise((res) => setTimeout(res, 180000)); // 3 دقائق
    }
  };

  // تصميم زر التفعيل الصغير الشفاف
menu.style.cssText = `
  position: fixed;
  bottom: 10px;
  left: 10px;
  background: rgba(0, 0, 0, 0.5);
  color: #fff;
  padding: 4px 8px;
  font-size: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  cursor: pointer;
  z-index: 9999;
  font-family: Arial;
`;
  document.body.appendChild(menu);
})();
