<template>
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="flex">
      <div class="-mr-12">
        <div class="bg-white py-10 lg:px-8 w-3/4">
          <div class="mx-auto max-w-3xl text-base leading-7 text-gray-700">
            <img
              src="https://feedbackup.com/images/customer-feedback-software-icon.png?v=1666348652120299795"
            />
            <h5
              class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl"
            >
              Manage Feedback
            </h5>
            <p class="mt-6 text-lg leading-8">
              Collect, sort, analyze, and follow up on customer feedback to
              figure out what's working and what needs to be changed in your
              product.
            </p>
          </div>
          <div class="mx-auto max-w-3xl text-base leading-7 text-gray-700 mt-7">
            <h5 class="mt-2 text-xl font-bold tracking-tight text-gray-900">
              Add Feedback Widgets
            </h5>
            <p class="mt-3 text-lg leading-8">
              Add a feedback form to your website as a popover or a button to
              collect feedback
            </p>
          </div>

          <div
            class="mx-auto max-w-3xl text-base leading-7 text-gray-700 sm:text-xl mt-4"
          >
            <h5
              class="mt-2 text-3xl font-bold tracking-tight text-gray-900 sm:text-xl"
            >
              Integrate with Other Tools
            </h5>
            <p class="mt-3 text-lg leading-8">
              Create a dedicated feedback tool and integrate it with popular
              project management software such as Projectsly
            </p>
          </div>
        </div>
        <div class="flex gap-3">
          <div>
            <button
              type="button"
              class="rounded-md bg-blue-600 px-16 py-5 ml-7 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            >
              Sign Up
            </button>

            <p class="ml-7 text-xs mt-1 text-gray-500">
              No creditcard required
            </p>
          </div>
          <div class="flex gap-5">
            <div class="text-gray-600 ml-3 mt-4">
              <p>or</p>
            </div>
            <div class="mt-3">
              <img
                class="inline-block h-8 w-8 rounded-full mr-2"
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAF8AAABfCAMAAAC5kuvHAAABFFBMVEX////qQzU0qFNChfT7vAUyfvS5z/bB0/qvx/ovp1D7uADqQTPqPzD7ugD/vQDpMB3pNST/+/QaokP4/Pn+9fT87OvpOSnrSj38wgD80n0mpUrd7uGr1rQ9q1nsYFbuc2v50tDpKxXvgXr0paHsWU762df75eP/9ubpOjb95bf94Kn+8NT7wjUZp1aWzKLp9Ottu3+CxJFYs25Kr2P1s6/wi4X3w8DtaF/nCwD4tWLtXDTxey/2nCPsUzfymZT8yVvvbTH0kCj5rxrd5/oXdPOOsfX8xEVzofNXkfHguR/G5M+utDd1rkeEr0NMqlDGtizUx2lXl988ksQzq0A5nJk1onM+mLI2oII+it49lLw1pWkmf+JWHcEYAAAESUlEQVRoge2XaWOaSBzG7QSSoAhkVLSjiBhjrzRBUdPdHmlr0ia2291ueuy23/97lMFrYA4HxFe7z5towvz+M8//GFIo/K/8VMXaBbjWGY3ddq+O1Wu741EnvzDVybhumZat66W5dN0Ov9fHk1zgrmfapXuUSiXbtLqd7ei1ccnUafYqhu3Vj7Mb1Xc91s6TIca1jHv3BFsnZFvHGfDHli1Fx2ew7qVNdb9nbnImFsFzU6VhJMoq26RSRx7fTbX55RFks1DtWanpWN6FFL5WT+vNkv9KBt+3s+Kl/KntFl/NbI5cdnu7xXfFlRNO5lCM2pXEj0wB2jJNu3fhXvTCD1Y8iCT+hNtWull3RyfLEVA9Gbk60eGyncUzX/fcSXK8VCft5XiVxR+z3dHNbp993IvovLL4msV0x2yfcJdM6rY0vtBlzfuSuOmr3Wey+L7H8sbubFi26e8r/aY/pPE62/kMelAs/p4MoOvZbm6W7peVxvN4gJKd2+4LR0qoxotYgGed3PCFR8UoQPHlOoIldV1I6rKsRFp7pLdzxB8VlYVWHpn8tkqvRyu+0ngbeaS7OeJx9azVeB0G8PKrnVAKyVcabx7mu/0HRSWmxlszj/8dVnqS4CtKkfc6Od2XFLnocZJfvuRt5fBKldLVlFgUS2+0/cdcvronJfWQWHRJ8Z9szb8mFr2j+Efb8vfer9ccnSb5ZR5enn8j4JdPt+fvEfxkdZbfbc9XRXxueebEz3n/u/Cf4Beo+iluzyfyu5P6J+pzF/0b4+9g/pD9m2p+Zpk/1Pw3Tis8Pmc+U3xyfibvL+MWzjj86QFT1LFUcv4n7l/jw1PN5xnE1oGYTybYUD4+BQCep+Jfi8on9v5j3IIQD1IeQFg+5Ptb6A2IBJsp8PuUPfvxBxYdZhh/LPBAC1Lwb6jymcYfmBtk3H5a4gFAZ9J4Krux6YMVjWjjzzUdO8SrUUp0dx0mH7lfJrxZWiRZQ9d0d02Tz4Qt9imBB5pcAMbIuKGf+ksDlDRNooio2qGrB6sJaT7Q0MYcMPBUdiMNECMAgBuqiPaelV2scyYfoEDg0ezzFWP3KvvhM5ZDoUfQ50Ro+hD9Led+pICR4kWEGXUfVFpDGD5/94UKwCiexX7YB4giAL/VXMU4n7WGGpzv5u7rz3gEuvZXanED4FKCEDpDfxjgD2h9VKR9JgPELsakfHaO10GwqF/efVMl3BGmQKy776qEO1gVJ1MABP6ZR1APhHjcBZkCaPBfldtZMTWzBYgKVZjb1QlAtgDox08ZfJiDYEMV8U7QksKH8gV9wJMmf93hRkvrEXLSvG8UmkG6I8AB74WVpzMknwUEUniz1PlA0iQEz9Jufi483yXog3SvqvEzAOEhNOhk3PtSlZkPIT0zMVuDiHHvZAkxcMKJjxazGf9ACCJnkAd8ofDGGoRXS+A4ThAM/UFrlt10gSpYuwD/Z/ULuLl7d4tR67oAAAAASUVORK5CYII="
                alt=""
              />
              <img
                class="inline-block h-8 w-8 rounded-full mr-2"
                src="data:image/png;base64,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"
                alt=""
              />
              <img
                class="inline-block h-8 w-8 rounded-full mr-2"
                src="data:image/png;base64,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"
                alt=""
              />
              <img
                class="inline-block h-8 w-8 rounded-full mr-2"
                src="data:image/jpeg;base64,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"
                alt=""
              />
            </div>
          </div>
        </div>
      </div>

      <div class="h-64 basis-1/2 mt-40">
        <img
          class="w-auto h-auto"
          src="https://media.slidesgo.com/storage/5083394/Effective-workflow.gif"
          alt="Your GIF"
        />
      </div>
    </div>
  </div>
</template>
